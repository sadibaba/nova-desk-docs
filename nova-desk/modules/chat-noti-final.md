## 📚 Complete Documentation - Chat + Notifications Module

---

# 💬 CHAT MODULE

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CHAT MODULE ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────────────────┐ │
│  │   Client    │◄──►│  WebSocket  │◄──►│      Socket.IO Server           │ │
│  │  (Frontend) │    │  (Socket.IO)│    │  (Real-time Events)              │ │
│  └─────────────┘    └─────────────┘    └─────────────────────────────────┘ │
│         │                  │                          │                    │
│         ▼                  ▼                          ▼                    │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                         REST API Layer                                  ││
│  │  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌─────────────────────┐ ││
│  │  │   Chat    │  │  Message  │  │   Follow  │  │   Message Request   │ ││
│  │  │ Controller│  │ Controller│  │ Controller│  │     Controller      │ ││
│  │  └───────────┘  └───────────┘  └───────────┘  └─────────────────────┘ ││
│  └─────────────────────────────────────────────────────────────────────────┘│
│                                    │                                         │
│                                    ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                         Service Layer                                   ││
│  │  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌─────────────────────┐ ││
│  │  │   Chat    │  │  Message  │  │   Follow  │  │  Message Request   │ ││
│  │  │  Service  │  │  Service  │  │  Service  │  │     Service        │ ││
│  │  └───────────┘  └───────────┘  └───────────┘  └─────────────────────┘ ││
│  └─────────────────────────────────────────────────────────────────────────┘│
│                                    │                                         │
│                                    ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                         Database Layer                                  ││
│  │  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌─────────────────────┐ ││
│  │  │   Chat    │  │  Message  │  │   Follow  │  │  Message Request   │ ││
│  │  │   Model   │  │   Model   │  │   Model   │  │     Model          │ ││
│  │  └───────────┘  └───────────┘  └───────────┘  └─────────────────────┘ ││
│  └─────────────────────────────────────────────────────────────────────────┘│
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔌 API Endpoints

### Base URL: `http://localhost:3800/api/v1`

### Chat Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/chat` | Get all user chats | ✅ |
| GET | `/chat/global` | Get global chat | ✅ |
| GET | `/chat/direct/:userId` | Get direct chat with user | ✅ |
| GET | `/chat/team/:teamId` | Get team chat | ✅ |
| GET | `/chat/unread-count` | Get total unread count | ✅ |
| GET | `/chat/:chatId` | Get chat by ID | ✅ |
| PUT | `/chat/:chatId/mark-read` | Mark chat as read | ✅ |

### Message Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/messages/chat/:chatId` | Get chat messages | ✅ |
| POST | `/messages` | Send message | ✅ |
| PUT | `/messages/:messageId` | Edit message | ✅ |
| DELETE | `/messages/:messageId` | Delete message | ✅ |
| PUT | `/messages/:messageId/read` | Mark message read | ✅ |
| POST | `/messages/:messageId/react` | Add reaction | ✅ |
| DELETE | `/messages/:messageId/react/:reactionId` | Remove reaction | ✅ |

### Follow Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/follow/:userId` | Follow user | ✅ |
| DELETE | `/follow/:userId` | Unfollow user | ✅ |
| GET | `/follow/followers` | Get followers | ✅ |
| GET | `/follow/following` | Get following | ✅ |
| GET | `/follow/status/:userId` | Get follow status | ✅ |
| GET | `/follow/mutual/:userId` | Get mutual followers | ✅ |

### Message Request Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/message-requests` | Get pending requests | ✅ |
| POST | `/message-requests/:userId` | Send request | ✅ |
| POST | `/message-requests/:requestId/accept` | Accept request | ✅ |
| POST | `/message-requests/:requestId/decline` | Decline request | ✅ |

---

## 📊 Database Schema

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
  reactions: [{
    user: ObjectId('User'),
    emoji: String,
    createdAt: Date
  }],
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

## 🔌 WebSocket Events (Socket.IO)

### Client → Server Events

| Event | Payload | Description |
|-------|---------|-------------|
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

### Server → Client Events

| Event | Payload | Description |
|-------|---------|-------------|
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

## 🔧 Services

### ChatService

| Method | Description |
|--------|-------------|
| `getUserChats(userId)` | Get all chats for user |
| `getChatMessages(chatId, userId, page, limit)` | Get messages with pagination |
| `sendMessage(chatId, senderId, content, replyTo, isRequest)` | Send message |
| `markChatAsRead(chatId, userId)` | Mark chat as read |

### FollowService

| Method | Description |
|--------|-------------|
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
|--------|-------------|
| `getPendingRequests(userId)` | Get pending requests |
| `sendRequest(fromId, toId, firstMessage)` | Send request |
| `acceptRequest(requestId, userId)` | Accept request |
| `declineRequest(requestId, userId)` | Decline request |

---

## 🧪 Testing

### Run Tests

```bash
k6 run tests/chat-notification-complete-test.js
```

### Test Coverage

| Feature | Status |
|---------|--------|
| User Registration | ✅ Pass |
| Browser Profiles | ✅ Pass |
| Mutual Follow | ✅ Pass |
| Private Chat | ✅ Pass |
| Team Chat | ✅ Pass |
| Notifications | ✅ Pass |

---

## 📁 File Structure

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

# 🔔 NOTIFICATIONS MODULE

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      NOTIFICATIONS MODULE ARCHITECTURE                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────────────────┐ │
│  │   Client    │◄──►│  WebSocket  │◄──►│      Socket.IO Server           │ │
│  │  (Frontend) │    │  (Socket.IO)│    │  (Real-time Events)              │ │
│  └─────────────┘    └─────────────┘    └─────────────────────────────────┘ │
│         │                  │                          │                    │
│         ▼                  ▼                          ▼                    │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                         REST API Layer                                  ││
│  │  ┌───────────────────────┐  ┌─────────────────────────────────────────┐ ││
│  │  │   Notification        │  │   Notification Settings                 │ ││
│  │  │   Controller          │  │   Controller                           │ ││
│  │  └───────────────────────┘  └─────────────────────────────────────────┘ ││
│  └─────────────────────────────────────────────────────────────────────────┘│
│                                    │                                         │
│                                    ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                         Service Layer                                   ││
│  │  ┌─────────────────────────────────────────────────────────────────────┐││
│  │  │                     NotificationService                            │││
│  │  │  • createNotification  • getUserNotifications  • markAsRead        │││
│  │  │  • markAllAsRead      • deleteNotification   • getStats           │││
│  │  │  • updateSettings     • registerDeviceToken   • unregisterDevice   │││
│  │  └─────────────────────────────────────────────────────────────────────┘││
│  └─────────────────────────────────────────────────────────────────────────┘│
│                                    │                                         │
│                                    ▼                                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                         Database Layer                                  ││
│  │  ┌─────────────────────────────────────────────────────────────────────┐││
│  │  │                     Notification Model                             │││
│  │  │  • recipient  • sender  • type  • title  • message                 │││
│  │  │  • resourceType  • resourceId  • isRead  • priority                │││
│  │  └─────────────────────────────────────────────────────────────────────┘││
│  │  ┌─────────────────────────────────────────────────────────────────────┐││
│  │  │                     NotificationSettings Model                     │││
│  │  │  • email  • push  • inApp  • categories  • quietHours  • dnd       │││
│  │  └─────────────────────────────────────────────────────────────────────┘││
│  └─────────────────────────────────────────────────────────────────────────┘│
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔌 API Endpoints

### Base URL: `http://localhost:3800/api/v1/notifications`

### Notification Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/` | Get notifications | ✅ |
| GET | `/unread/count` | Get unread count | ✅ |
| GET | `/stats` | Get notification stats | ✅ |
| PATCH | `/:id/read` | Mark as read | ✅ |
| POST | `/read-all` | Mark all as read | ✅ |
| DELETE | `/:id` | Delete notification | ✅ |
| DELETE | `/` | Delete all notifications | ✅ |

### Settings Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/settings` | Get notification settings | ✅ |
| PUT | `/settings` | Update settings | ✅ |
| POST | `/settings/device` | Register device | ✅ |
| DELETE | `/settings/device` | Unregister device | ✅ |
| POST | `/settings/dnd` | Toggle Do Not Disturb | ✅ |

---

## 📊 Database Schema

### Notification Model

```javascript
{
  recipient: ObjectId('User'),          // Who receives
  sender: ObjectId('User'),             // Who triggers
  senderBrowser: ObjectId('Browser'),
  type: String,                         // like, comment, follow, team_invite, task_assigned, etc.
  title: String,                        // Notification title
  message: String,                      // Notification message
  preview: String,                      // Short preview for push
  resourceType: String,                 // post, team, task, chat, etc.
  resourceId: ObjectId,                 // Related resource ID
  resourceModel: String,                // Model name
  actionUrl: String,                    // Frontend URL
  metadata: Object,                     // Additional data
  priority: 'low' | 'medium' | 'high' | 'critical',
  isRead: Boolean,                      // Read status
  isSeen: Boolean,                      // Seen status
  isDeleted: Boolean,                   // Soft delete
  emailSent: Boolean,                   // Email sent
  pushSent: Boolean,                    // Push sent
  expiresAt: Date,                      // Expiry
  readAt: Date,                         // Read time
  createdAt: Date,
  updatedAt: Date
}
```

### NotificationSettings Model

```javascript
{
  user: ObjectId('User'),
  
  // Email preferences
  email: {
    enabled: Boolean,
    digest: 'instant' | 'hourly' | 'daily' | 'weekly'
  },
  
  // Push preferences
  push: {
    enabled: Boolean,
    sound: Boolean,
    badge: Boolean
  },
  
  // In-app preferences
  inApp: {
    enabled: Boolean,
    sound: Boolean
  },
  
  // Category wise preferences
  categories: {
    likes: Boolean,
    comments: Boolean,
    replies: Boolean,
    shares: Boolean,
    follows: Boolean,
    teamInvites: Boolean,
    teamJoinRequests: Boolean,
    teamMemberChanges: Boolean,
    teamRoleChanges: Boolean,
    taskAssignments: Boolean,
    taskUpdates: Boolean,
    taskOverdue: Boolean,
    directMessages: Boolean,
    mentions: Boolean,
    meetingReminders: Boolean,
    meetingUpdates: Boolean,
    systemAlerts: Boolean,
    announcements: Boolean,
    contactMessages: Boolean
  },
  
  // Quiet hours
  quietHours: {
    enabled: Boolean,
    start: String,    // '22:00'
    end: String,      // '08:00'
    timezone: String  // 'UTC'
  },
  
  // Do Not Disturb
  doNotDisturb: {
    enabled: Boolean,
    until: Date
  },
  
  // Device tokens for push
  deviceTokens: [{
    token: String,
    platform: 'ios' | 'android' | 'web',
    lastUsed: Date
  }],
  
  createdAt: Date,
  updatedAt: Date
}
```

---

## 🔌 WebSocket Events

### Server → Client Events

| Event | Payload | Description |
|-------|---------|-------------|
| `notification:new` | `Notification` | New notification received |
| `notification:unreadCount` | `{ count }` | Updated unread count |

### Client → Server Events

| Event | Payload | Description |
|-------|---------|-------------|
| `notification:read` | `{ notificationId }` | Mark as read |
| `notification:read-all` | `{}` | Mark all as read |
| `notification:get-unread` | `{}` | Get unread count |

---

## 🔧 Services

### NotificationService

| Method | Description |
|--------|-------------|
| `createNotification(data)` | Create and send notification |
| `getUserSettings(userId)` | Get user settings |
| `updateSettings(userId, updates)` | Update settings |
| `getUserNotifications(userId, options)` | Get notifications with pagination |
| `markAsRead(notificationId, userId)` | Mark as read |
| `markAllAsRead(userId)` | Mark all as read |
| `deleteNotification(notificationId, userId)` | Delete notification |
| `deleteAllNotifications(userId)` | Delete all notifications |
| `registerDeviceToken(userId, token, platform)` | Register device |
| `unregisterDeviceToken(userId, token)` | Unregister device |
| `getStats(userId, days)` | Get notification stats |

---

## 🧪 Testing

### Run Tests

```bash
k6 run tests/chat-notification-complete-test.js
```

### Test Coverage

| Feature | Status |
|---------|--------|
| Get Notifications | ✅ Pass |
| Get Unread Count | ✅ Pass |
| Get Settings | ✅ Pass |
| Update Settings | ✅ Pass |
| Get Stats | ✅ Pass |
| Mark as Read | ✅ Pass |
| Mark All Read | ✅ Pass |

---

## 📁 File Structure

```
src/modules/notifications/
├── controllers/
│   ├── notification.controller.js
│   └── notificationSettings.controller.js
├── models/
│   ├── notification.model.js
│   └── notificationSettings.model.js
├── routes/
│   └── notification.routes.js
├── services/
│   └── notification.service.js
├── sockets/
│   └── notification.socket.js
├── helpers/
│   └── notificationHelpers.js
└── notifications.module.js
```

---

## 🔧 Notification Types

| Type | Category | Priority | Description |
|------|----------|----------|-------------|
| `like` | Social | Low | Someone liked your post |
| `comment` | Social | Medium | Someone commented on your post |
| `reply` | Social | Medium | Someone replied to your comment |
| `share` | Social | Low | Someone shared your post |
| `follow` | Social | Low | Someone followed you |
| `team_invite` | Team | High | Invited to team |
| `team_join_request` | Team | High | Join request to team |
| `team_join_approved` | Team | High | Join request approved |
| `team_member_added` | Team | Medium | Added to team |
| `team_member_removed` | Team | Medium | Removed from team |
| `team_role_changed` | Team | Medium | Role changed |
| `task_assigned` | Task | High | Task assigned |
| `task_completed` | Task | Medium | Task completed |
| `task_overdue` | Task | High | Task overdue |
| `task_status_changed` | Task | Medium | Task status changed |
| `message_received` | Chat | Medium | New message |
| `message_mention` | Chat | High | Mention in message |
| `meeting_scheduled` | Meeting | High | Meeting scheduled |
| `meeting_reminder` | Meeting | High | Meeting reminder |
| `meeting_changed` | Meeting | Medium | Meeting changed |
| `system_alert` | System | Critical | System alert |
| `announcement` | System | Medium | Announcement |
| `contact_message` | Contact | High | Contact message |
| `owner_message` | Contact | High | Owner message |

---

## 🔑 Key Concepts

### 1. Lazy Creation
- Browser profiles created on first access
- Notification settings lazily created
- Chats lazily created on first message

### 2. Follow System
- Mutual follow required for direct messages
- Follow status: `none` | `following` | `mutual`

### 3. Real-time Updates
- WebSocket for instant notifications
- Online/offline status tracking
- Typing indicators

### 4. Push Notifications
- Device token registration
- Platform support: iOS, Android, Web

---

## ✅ MODULES COMPLETE!

| Module | Status |
|--------|--------|
| auth Module | ✅ Complete |
| Team Module | ✅ Complete |
| Code Module | ✅ Complete |
| Browser Module | ✅ Complete |
| Chat Module | ✅ Complete |
| Notifications Module | ✅ Complete |

---

**🎉 All Modules Ready for Production!**