# NovaDesk Challenges — Final 500-Question Blueprint

Status: **500-question beta bank generated and seeded** (pending human content QA).
Scope: first production batch = **500 questions**. Then review, refine and add 500 more.

## 1. Final recommendation

Start with **500**, not 1000:

| Block | Count | Grading |
|---|---:|---|
| Syntax / fundamentals | 300 | Automatic |
| Logic / coding | 120 | Hidden tests |
| System design / architecture | 50 | Human rubric |
| Debugging / reasoning | 30 | Tests + rubric |
| **Total** | **500** | |

Why 500: it proves the rank, review queue, rubric and UX before spending weeks
authoring 500 more. Do not publish 1000 mediocre questions.

## 2. 300 syntax questions

All auto-graded. Mix:

- 80 JavaScript / TypeScript
- 50 Python
- 40 C / C++
- 40 SQL
- 30 React / Next.js
- 30 Node / Express
- 15 Git / HTTP
- 15 Docker / Linux basics

Formats:

- 45% multiple choice
- 25% output prediction
- 15% find the bug
- 10% fill in the blank
- 5% complexity / concept matching

Rules:

- One correct answer.
- Every wrong option must be plausible.
- Randomize option order.
- No copied LeetCode/paid content.
- Explanation shown after submission.

## 3. 200 logic / design questions

### 120 coding / logic (auto + explanation)

Topics:

- Arrays, strings, hash maps (30)
- Two pointers / sliding window (20)
- Stack, queue, linked list (20)
- Trees, graphs, BFS/DFS (20)
- Recursion / backtracking (10)
- Sorting, binary search, intervals (10)
- Basic DP (10)

Grading:

- Hidden tests (60%)
- Visible examples (20%)
- Explanation rubric (20%)
- Time/memory limit.
- Best score per question; no negative points.

### 50 system design (human rubric)

Must cover:

- Requirements and assumptions
- API and data model
- Architecture and data flow
- Scaling and bottlenecks
- Failure handling and observability
- Security and multi-tenancy
- Trade-offs and next steps

Rubric: 8 dimensions × 0–4 = 32. Pass = 18+ and no critical security flaw.
Two reviewers; average score; appeal path.

### 30 debugging / reasoning (tests + rubric)

- Broken code: find and fix.
- Logs/metrics: identify root cause.
- Performance: explain bottleneck.
- Security: identify vulnerability.
- Answer includes root cause, fix, prevention.

## 4. Rank and points — final rules

Global rank uses real `Browser.stats.totalPoints`:

```text
rank = 1 + count(users with more points,
                 or same points and more completed challenges)
```

Points:

- easy: 2
- medium: 4
- hard: 6
- extreme: 10
- design: 4–10, based on rubric percentage
- debugging: 4–6

These match the existing challenge point map. Increasing the scale later requires
a migration; do not mix old and new values.

One score per challenge (best attempt). No fake leaderboard rows. A user with
zero points is **Unranked**, not `#1`.

Tie-breakers:

1. total points
2. completed challenges
3. design rubric score
4. earliest completion

Leaderboard APIs:

```text
GET /api/v1/browser/challenges/leaderboard/global?limit=20
GET /api/v1/browser/challenges/stats/user
```

## 5. Answer review workflow

```text
Student submits
  → automatic checks (tests/MCQ)
  → if design: review queue
  → reviewer scores rubric
  → second reviewer for appeal/score > threshold
  → points awarded
  → leaderboard updates
```

Reviewer UI needs:

- question + student answer
- rubric checkboxes
- comment box
- score preview
- approve / request changes / reject
- audit log

AI may pre-label, but final score is human for open answers. AI confidence low
→ mandatory human review.

## 6. Question schema (minimum)

```text
id, slug, title, prompt
type: mcq | output | bug | coding | design | debugging
topic, difficulty, points
language(s)
starterCode
visibleExamples[]
hiddenTests[]
rubric[]
sampleAnswer
explanation
tags[]
status: draft | review | published | archived
author, reviewer, version
```

## 7. Content quality gate

Before publish:

- [ ] Two people solved/validated it.
- [ ] Hidden tests cover edge cases.
- [ ] Ambiguity removed.
- [ ] No more than one valid MCQ answer.
- [ ] Design rubric and sample answer exist.
- [ ] Copyright/originality checked.
- [ ] Explanation is beginner-friendly.
- [ ] Accessibility: no colour-only meaning, no emoji-only labels.
- [ ] Difficulty calibrated against 5 testers.

## 8. 8-week content plan

- Week 1: schema, 50 syntax, 10 coding.
- Week 2: 100 syntax, 20 coding.
- Week 3: 150 syntax, 20 coding, 10 design.
- Week 4: finish 300 syntax, 30 coding, 15 design.
- Week 5: 40 coding, 15 design, 10 debugging.
- Week 6: 20 coding, 10 design, 10 debugging.
- Week 7: review 500, fix failures.
- Week 8: pilot with 10 students, calibrate points.

## 9. Acceptance criteria for launch

- 0 fake leaderboard entries.
- Rank matches manual calculation for 10 test users.
- 300 syntax questions auto-grade correctly.
- 50 design answers reviewed by two reviewers with <10% score variance.
- No question has >5% invalid-answer reports.
- Every published question has explanation and rubric.
- Mobile and desktop usable.
- Admin can archive a bad question immediately.

## 10. Generated bank

The beta bank lives at `Backend/src/seed/generated-500.json`:

- 300 syntax MCQs
- 120 DSA coding challenges
- 50 system-design text challenges with rubrics
- 30 logical/debugging text challenges with rubrics

It is deterministic and generated by `scripts/generate_challenge_bank.py`. Human
review is still required before calling any item final; generated content should
not be treated as professionally authored without QA.

## 11. Not in this batch

- 1000 questions at once.
- AI-only grading of design answers.
- Team challenges.
- Paid contests.
- Plagiarism detection beyond basic duplicate-answer checks.
