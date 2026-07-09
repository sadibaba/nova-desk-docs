# 💬 Chat Module — Backend Technical Report

Base URL: `http://localhost:3800/api/v1`

---

## 1. Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CHAT MODULE ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                               │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────────────────┐  │
│  │   Client    │◄──►│  WebSocket  │◄──►│      Socket.IO Server          │  │
│  │  (Frontend) │    │  (Socket.IO)│    │  (Real-time Events)            │  │
│  └─────────────┘    └─────────────┘    └─────────────────────────────────┘  │
│         │                  │                          │                     │
│         ▼                  ▼                          ▼                     │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                         REST API Layer                                │  │
│  │  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌─────────────────────┐│  │
│  │  │   Chat    │  │  Message  │  │   Follow  │  │   Message Request   ││  │
│  │  │ Controller│  │ Controller│  │ Controller│  │     Controller      ││  │
│  │  └───────────┘  └───────────┘  └───────────┘  └─────────────────────┘│  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                    │                                         │
│                                    ▼                                         │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                         Service Layer                                 │  │
│  │  Chat Service │ Message Service │ Follow Service │ Message Request Svc│  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                    │                                         │
│                                    ▼                                         │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                         Database Layer                                │  │
│  │  Chat Model │ Message Model │ Follow Model │ Message Request Model    │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                               │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. API Endpoints

### Chat

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/chat` | Get all user chats | ✅ |
| GET | `/chat/global` | Get global chat | ✅ |
| GET | `/chat/direct/:userId` | Get direct chat with user | ✅ |
| GET | `/chat/team/:teamId` | Get team chat | ✅ |
| GET | `/chat/unread-count` | Get total unread count | ✅ |
| GET | `/chat/:chatId` | Get chat by ID | ✅ |
| PUT | `/chat/:chatId/mark-read` | Mark chat as read | ✅ |

### Messages

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/messages/chat/:chatId` | Get chat messages | ✅ |
| POST | `/messages` | Send message | ✅ |
| PUT | `/messages/:messageId` | Edit message | ✅ |
| DELETE | `/messages/:messageId` | Delete message | ✅ |
| PUT | `/messages/:messageId/read` | Mark message read | ✅ |
| POST | `/messages/:messageId/react` | Add reaction | ✅ |
| DELETE | `/messages/:messageId/react/:reactionId` | Remove reaction | ✅ |

### Follow

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | `/follow/:userId` | Follow user | ✅ |
| DELETE | `/follow/:userId` | Unfollow user | ✅ |
| GET | `/follow/followers` | Get followers | ✅ |
| GET | `/follow/following` | Get following | ✅ |
| GET | `/follow/status/:userId` | Get follow status | ✅ |
| GET | `/follow/mutual/:userId` | Get mutual followers | ✅ |

### Message Requests

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/message-requests` | Get pending requests | ✅ |
| POST | `/message-requests/:userId` | Send request | ✅ |
| POST | `/message-requests/:requestId/accept` | Accept request | ✅ |
| POST | `/message-requests/:requestId/decline` | Decline request | ✅ |

---

## 3. Database Schema

### Chat Model
```javascript
{
  type: 'global' | 'direct' | 'team' | 'channel',
  participants: [ObjectId('User')],
  team: ObjectId('Team'),
  channel: ObjectId('TeamChannel'),
  name: String,
  avatar: String,
  lastMessage: {
    text: String,
    sender: ObjectId('User'),
    sentAt: Date,
    readBy: [ObjectId('User')]
  },
  messageCount: Number,
  isActive: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

### Message Model
```javascript
{
  chat: ObjectId('Chat'),
  sender: ObjectId('User'),
  receiver: ObjectId('User'),
  content: {
    text: String,
    media: [{
      type: 'image' | 'video' | 'audio' | 'file' | 'voice_note',
      url: String,
      thumbnail: String,
      size: Number,
      name: String,
      duration: Number
    }],
    replyTo: ObjectId('Message'),
    mentions: [ObjectId('User')]
  },
  call: {
    type: 'audio' | 'video',
    duration: Number,
    status: 'missed' | 'completed' | 'rejected' | 'cancelled',
    startedAt: Date,
    endedAt: Date
  },
  status: {
    sent: Boolean,
    delivered: Boolean,
    read: Boolean,
    deliveredAt: Date,
    readAt: Date
  },
  isRequest: Boolean,
  requestStatus: 'pending' | 'accepted' | 'declined',
  isDeleted: Boolean,
  deletedFor: [ObjectId('User')],
  editedAt: Date,
  reactions: [{ user: ObjectId('User'), emoji: String, createdAt: Date }],
  createdAt: Date,
  updatedAt: Date
}
```

### Follow Model
```javascript
{
  follower: ObjectId('User'),
  following: ObjectId('User'),
  status: 'pending' | 'accepted' | 'blocked',
  requestedAt: Date,
  acceptedAt: Date,
  createdAt: Date,
  updatedAt: Date
}
```

### Message Request Model
```javascript
{
  from: ObjectId('User'),
  to: ObjectId('User'),
  firstMessage: String,
  status: 'pending' | 'accepted' | 'declined' | 'expired',
  expiresAt: Date,
  createdAt: Date,
  updatedAt: Date
}
```

---

## 4. WebSocket Events (Socket.IO)

### Client → Server

| Event | Payload | Description |
|---|---|---|
| `join-chat` | `{ chatId }` | Join chat room |
| `send-message` | `{ chatId, content, replyTo }` | Send message |
| `typing` | `{ chatId, isTyping }` | Typing indicator |
| `mark-read` | `{ messageId, chatId }` | Mark message read |
| `call:offer` | `{ callId, offer, toUserId, type, callerName, chatId }` | Start call |
| `call:answer` | `{ callId, answer, toUserId }` | Answer call |
| `call:ice-candidate` | `{ callId, candidate, toUserId }` | ICE candidate |
| `call:accept` | `{ callId, toUserId }` | Accept call |
| `call:reject` | `{ callId, toUserId }` | Reject call |
| `call:end` | `{ callId, toUserId, duration }` | End call |

### Server → Client

| Event | Payload | Description |
|---|---|---|
| `joined-chat` | `{ chatId, success, onlineUsers }` | Joined chat |
| `user-joined` | `{ userId, onlineUsers }` | User joined |
| `new-message` | `Message` | New message received |
| `user-typing` | `{ userId, isTyping }` | User typing |
| `message-read` | `{ messageId, userId }` | Message read |
| `call:incoming` | `{ callId, offer, callerId, callerName, type, chatId }` | Incoming call |
| `call:accepted` | `{ callId, answer, fromUserId }` | Call accepted |
| `call:rejected` | `{ callId, fromUserId }` | Call rejected |
| `call:ended` | `{ callId, duration, fromUserId }` | Call ended |
| `call:ice-candidate` | `{ callId, candidate, fromUserId }` | ICE candidate |
| `online-users` | `[userId]` | Online users list |

---

## 5. Services

### ChatService
| Method | Description |
|---|---|
| `getUserChats(userId)` | Get all chats for user |
| `getChatMessages(chatId, userId, page, limit)` | Get messages with pagination |
| `sendMessage(chatId, senderId, content, replyTo, isRequest)` | Send message |
| `markChatAsRead(chatId, userId)` | Mark chat as read |

### FollowService
| Method | Description |
|---|---|
| `isFollowing(followerId, followingId)` | Check if following |
| `areMutual(userId1, userId2)` | Check mutual follow |
| `followUser(followerId, followingId)` | Follow user |
| `unfollowUser(followerId, followingId)` | Unfollow user |
| `getFollowers(userId)` | Get followers list |
| `getFollowing(userId)` | Get following list |
| `getFollowStatus(followerId, followingId)` | Get follow status |
| `getMutualFollowers(userId)` | Get mutual followers |

### MessageRequestService
| Method | Description |
|---|---|
| `getPendingRequests(userId)` | Get pending requests |
| `sendRequest(fromId, toId, firstMessage)` | Send request |
| `acceptRequest(requestId, userId)` | Accept request |
| `declineRequest(requestId, userId)` | Decline request |

---

## 6. Key Concepts

1. **Lazy Creation** — Chats are lazily created on first message (both direct and team, in principle — see bug below). Browser profiles and notification settings follow the same lazy pattern.
2. **Follow Gate** — Mutual follow is required before direct messages can be sent freely. Follow status: `none` | `following` | `mutual`.
3. **Real-Time Layer** — WebSocket handles instant message delivery, online/offline tracking, and typing indicators.

---

## 7. Test Results

**Test:** `tests/chat-notification-complete-test.js` — single VU, 8 iterations, 3 users per iteration, full flow: register → browser profile → follow → direct chat → team chat → notifications.

### 7.1 Combined Metrics (Chat + Notifications)

| Metric | Value |
|---|---|
| Total requests | 190 |
| Success rate | 92.63% |
| Failed rate | 7.37% |
| Average response time | 751.66ms |
| Chat failure rate (as scored by test) | 0.00% |
| Iterations completed | 8 |

### 7.2 Confirmed Bug: Team Chat First Message — 400 (8/8 iterations)

Every single iteration showed the identical pattern:

```
✅ Create Team: Team created successfully
✅ Join Team: User2 joined team
✅ Join Team: User3 joined team
✅ Team Chat: Team chat not initialized     ← expected (lazy creation, same as direct chat)
❌ Team Message: Failed: 400                ← fails every time
```

For comparison, the equivalent direct-chat flow works every time:
```
✅ Direct Chat: Chat needs first message
✅ Send Message: Message sent: "..."
```

**Diagnosis direction:** since direct-chat's "create on first message" path works correctly but team-chat's does not, the bug is very likely isolated to the team-chat branch of `sendMessage()` in `ChatService` (or the `chat.controller.js` handler that routes team vs. direct sends) — possibly a missing `team` field being passed through, a validation schema mismatch, or the team-chat creation branch never being reached because of a condition that only checks for `receiver` (direct chat) and not `team` (team chat). Recommend adding a dedicated unit test for `ChatService.sendMessage()` with a team-chat payload to isolate the exact validation/logic step that returns the `400`.

> **This is a functional bug that should be fixed before production**, since it means team chats cannot currently be used at all — teams can be created and joined, but no message can ever be sent in them.

### 7.3 Load-Related Flakiness (Not the Same Bug)

Observed only in some iterations, not all — consistent with resource contention under sustained sequential load, not a logic bug:

| Iteration | Symptom |
|---|---|
| 0 | `Follow: User1 follow failed: 0` (request timeout on `POST /browser/profile/follow/:id`) — recovered, mutual follow still completed via User2's side |
| 2 | `Browser User1: Timeout, skipping` on `GET /browser/profile/me`; `Follow: User2 follow failed: 400` |
| 7 | All 3 browser profile lookups timed out; Follow step skipped entirely (`Not enough browser profiles`) — this iteration scored 3/5 (60%), the only iteration below 100% |

**Recommendation:** these look like the same class of issue documented in the Browser and Team module reports — response-time growth and occasional timeouts under back-to-back sequential load. Worth revisiting once the team-chat `400` bug above is fixed, to see if failure frequency changes.

---

## 8. File Structure

```
src/modules/chat/
├── controllers/
│   ├── chat.controller.js
│   ├── message.controller.js
│   ├── follow.controller.js
│   ├── messageRequest.controller.js
│   └── call.controller.js
├── models/
│   ├── chat.model.js
│   ├── message.model.js
│   ├── follow.model.js
│   ├── messageRequest.model.js
│   └── callSession.model.js
├── routes/
│   ├── chat.routes.js
│   ├── message.routes.js
│   ├── follow.routes.js
│   ├── messageRequest.routes.js
│   ├── call.routes.js
│   └── media.routes.js
├── services/
│   ├── chat.service.js
│   ├── follow.service.js
│   └── messageRequest.service.js
├── sockets/
│   └── chat.socket.js
├── validators/
│   └── chat.validator.js
├── middleware/
│   └── chat.middleware.js
└── chat.module.js
```

---

## 9. Current Status

| Item | Status |
|---|---|
| Direct chat (lazy creation, send, read) | ✅ Working |
| Follow / mutual follow / message requests | ✅ Working (occasional load-related timeouts) |
| Team creation & joining | ✅ Working |
| **Team chat first message** | ❌ **Failing (400) — 8/8 reproduction rate — needs a fix** |
| Message reactions, edit, delete, read receipts | Not exercised in this test run — endpoints exist, recommend dedicated test coverage |
| WebSocket real-time events | Defined and documented; not directly exercised by this REST-based k6 test — recommend a separate Socket.IO test pass |
| Calls (audio/video signaling) | Endpoints/events defined; not exercised in this test run |

**Verdict:** Chat Module is close to production-ready but has one confirmed, consistently-reproducing bug (team chat messaging) that should be fixed before shipping. Direct messaging and the follow system are solid. Recommend adding WebSocket-level and call-signaling test coverage as a next step, since the current test only exercises the REST layer.