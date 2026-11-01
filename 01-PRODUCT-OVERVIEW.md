# 01 - Product Overview

## The problem

A student developer usually works across separate tools:

- an editor for code
- a repository for source control
- a task board for team projects
- a chat app for coordination
- a challenge site for practice
- a notes app for links and decisions
- a separate portfolio site for job applications

The context switching is expensive, especially for students who are still
learning how to plan and finish a project.

## The promise

NovaDesk puts a student's coding practice, team project, and public proof of
work into one browser workspace. It does not try to replace a professional IDE
or a full enterprise collaboration suite. It aims to be the first place a
student opens when they want to build, collaborate, and show the result.

## Primary users

### 1. Computer science students

They need to practice coding, work on semester projects, and build a portfolio
before internships. They usually have limited setup time, no paid cloud budget,
and a mix of Windows, Linux, and low-spec machines.

### 2. Small student teams

They need a shared place for tasks, files, discussion, and a final project
record. They do not need enterprise permissions or procurement.

### 3. Early-career job seekers

They need a credible public page that shows projects, source links, live links,
their stack, and a way to contact them.

## Secondary users

- bootcamp learners
- teachers or mentors running a small cohort
- freelance beginners who need a simple project workspace
- developers who want a browser fallback when their local environment fails

## Core user journeys

### Journey A - practice and improve

1. Register or log in.
2. Open the browser workspace.
3. Pick a coding challenge.
4. Read the problem, write code, run it.
5. See progress, points, and the portfolio record.

### Journey B - run a team project

1. Create a team.
2. Invite or approve members.
3. Create tasks and assign them.
4. Discuss in team chat.
5. Store project files and links.
6. Track status and activity.
7. Finish with a visible project record.

### Journey C - build a portfolio

1. Open the portfolio.
2. Add profile details and social links.
3. Add projects with role, stack, source, live link, and screenshots.
4. Publish public contact details.
5. Share the portfolio with a recruiter.

### Journey D - operate and moderate

1. Admin logs in.
2. Reviews users, teams, challenges, reports, and audit logs.
3. Updates settings or suspends an account.
4. Records the action in the audit trail.

## Product principles

1. **One tab, fewer jumps.** Related work stays close together.
2. **Student-first.** Free tier, low setup, and a clear learning path.
3. **Show the work.** The portfolio and project records are part of the flow.
4. **Honest limits.** No fake enterprise promises and no hidden encryption.
5. **Graceful failure.** If the server is down, the user should see a clear
   message, not a raw framework error.
6. **Earn trust through operations.** Backups, moderation, support, and
   security matter more than another feature card.

## Scope boundaries

NovaDesk currently does not aim to be:

- a replacement for VS Code for professional teams
- a full CI/CD platform
- a cloud VM provider by default
- an end-to-end encrypted messenger
- a payment processor
- a marketplace
- an enterprise identity provider
- a storage provider with unlimited quotas

Optional integrations exist, but they are not required for the core product.

## Differentiation

The combination matters more than any individual feature:

- coding practice
- team execution
- a public portfolio
- a student-friendly free tier
- a desktop-style browser experience

The product should be judged by whether a student can move from "I want to
build something" to "I have a project and a page to show" with less friction.

## What not to add yet

- more games
- more social surfaces
- more admin settings
- a payment system without a pricing decision
- a cloud IDE without isolation and cost controls
- enterprise SSO
- a marketplace
- blockchain or token features

Each addition increases the surface area that must be secured, tested, and
supported.
