# Local Development Setup

## Purpose

This document describes the local development environment for FastHire.

Goals:

* easy setup
* low cost
* fast development
* AI-friendly workflow

---

# Development Machine

Recommended:

Windows 11

or

MacOS

Linux is optional.

---

# Required Software

Install:

* Git
* Node.js
* VS Code

Optional:

* Cursor
* Windsurf

---

# Step 1. Install Git

Download:

https://git-scm.com

Verify:

git --version

Expected:

git version x.x.x

---

# Step 2. Install Node.js

Download:

https://nodejs.org

Use:

LTS version

Verify:

node -v

npm -v

---

# Step 3. Install VS Code

Download:

https://code.visualstudio.com

---

# Recommended Extensions

Install:

ESLint

Prettier

Tailwind CSS IntelliSense

GitLens

Error Lens

PostgreSQL

DotENV

Path Intellisense

---

# Optional AI Extensions

Cursor

Continue

Cline

Roo Code

Use only one actively.

Avoid AI extension conflicts.

---

# Project Structure

Repository:

FastHire

Structure:

docs/

app/

components/

lib/

hooks/

types/

public/

supabase/

---

# Step 4. Clone Repository

Example:

git clone REPOSITORY_URL

cd FastHire

---

# Step 5. Install Dependencies

Run:

npm install

---

# Step 6. Environment Variables

Create:

.env.local

Required:

NEXT_PUBLIC_SUPABASE_URL=

NEXT_PUBLIC_SUPABASE_ANON_KEY=

SUPABASE_SERVICE_ROLE_KEY=

OPENAI_API_KEY=

POSTHOG_KEY=

SENTRY_DSN=

---

# Environment Rules

Never commit:

.env.local

Never share:

* API keys
* service role keys

---

# Step 7. Install Supabase CLI

Documentation:

https://supabase.com/docs/guides/cli

Verify:

supabase --version

---

# Step 8. Start Development

Run:

npm run dev

Expected:

http://localhost:3000

---

# Git Workflow

Main Branch:

main

Development Branch:

develop

Feature Branches:

feature/auth

feature/profile

feature-swipes

feature-chat

---

# Commit Rules

Good:

feat: add candidate profile

fix: resolve chat bug

docs: update architecture

refactor: simplify auth flow

Bad:

update

fix

changes

test

---

# Pull Request Rules

Every feature should:

* compile successfully
* pass linting
* not break existing functionality

---

# Code Formatting

Use:

Prettier

Automatically format on save.

---

# Linting

Run:

npm run lint

Fix all errors before commit.

---

# Type Safety

Run:

npm run type-check

No TypeScript errors allowed.

---

# Development Rules

Always:

* small commits
* small features
* frequent pushes

Avoid:

* giant changes
* massive refactors

---

# AI Development Workflow

Before generating code:

1. Read architecture.md
2. Read database.md
3. Read vibe_coding_rules.md
4. Read ai_context.md

Only then generate code.

---

# Vibe Coding Workflow

For every feature:

Step 1

Create task.

Step 2

Generate code.

Step 3

Review generated code.

Step 4

Run locally.

Step 5

Commit.

Step 6

Push.

Never skip testing.

---

# Backup Strategy

GitHub is the primary backup.

Push code daily.

Do not store important work only locally.

---

# Success Criteria

Development environment is ready when:

* Git installed
* Node installed
* VS Code installed
* Repository cloned
* Dependencies installed
* Supabase connected
* Local server running

Then application development can begin.
