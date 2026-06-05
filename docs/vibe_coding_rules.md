# Vibe Coding Rules

## Purpose

This document defines strict rules for AI-assisted development.

All AI tools must follow these rules when generating code, architecture, database migrations, UI components, or documentation.

Applicable to:

* ChatGPT
* Claude
* Qwen
* Lovable
* Cursor
* Windsurf
* Cline
* Roo Code

---

# General Principles

## Rule #1

Always prefer simplicity over complexity.

Bad:

* microservices
* event buses
* CQRS
* over-engineering

Good:

* monolith
* clear structure
* readable code

---

## Rule #2

Build only what is required now.

Avoid:

* future abstractions
* unnecessary layers
* speculative architecture

---

## Rule #3

Every generated feature must be production-ready.

Never generate:

* demo code
* mock security
* fake validation

---

# Project Stack

Frontend:

* Next.js 15
* TypeScript
* TailwindCSS
* Shadcn UI

Backend:

* Supabase

Database:

* PostgreSQL

Hosting:

* Vercel

Analytics:

* PostHog

Monitoring:

* Sentry

AI:

* OpenAI

No alternative stack should be proposed unless explicitly requested.

---

# Coding Rules

## TypeScript

Always:

* use TypeScript
* use strict mode
* use explicit types

Avoid:

* any
* unknown without validation

---

## React

Prefer:

* Server Components
* Server Actions

Avoid:

* unnecessary client components
* unnecessary state

---

## Components

Each component must:

* have a single responsibility
* be reusable
* be typed

Maximum file size:

* 300 lines

If larger:

* split component

---

## Imports

Always use aliases.

Example:

```typescript
import { Button } from "@/components/ui/button";
```

Never use long relative imports.

Bad:

```typescript
../../../../components
```

---

# Database Rules

Every table must contain:

* id
* created_at
* updated_at

Use UUID for primary keys.

---

## Migrations

Never edit existing migrations.

Always create new migrations.

---

## Queries

Avoid:

* N+1 queries
* duplicate queries

Prefer:

* joins
* views
* pagination

---

# Security Rules

Security has higher priority than speed.

---

## Authentication

Use:

* Supabase Auth

Never:

* build custom authentication

---

## Authorization

Always enforce:

* Row Level Security

Never:

* disable RLS

---

## Secrets

Never expose:

* service role key
* API secrets
* private tokens

Use:

* environment variables

---

## Validation

Validate:

* form data
* file uploads
* API requests

Use:

* Zod

---

## File Uploads

Allowed:

* PDF
* DOCX
* JPEG
* PNG
* MP4

Validate:

* mime type
* file size

Maximum sizes:

Resume:

* 10 MB

Video:

* 100 MB

---

# API Rules

Use:

* Server Actions

Avoid:

* unnecessary REST endpoints

---

## Rate Limiting

Apply rate limits to:

* login
* registration
* messaging
* uploads

---

# UI Rules

Design style:

* modern
* premium
* minimalistic

---

## Mobile First

All pages must work on:

* mobile
* tablet
* desktop

---

## Accessibility

Must support:

* keyboard navigation
* screen readers
* sufficient contrast

---

# Performance Rules

Target Lighthouse:

* Performance 90+
* Accessibility 90+
* Best Practices 90+
* SEO 90+

---

## Images

Use:

* Next.js Image

Never:

* raw img tags

---

## Lists

Use pagination or infinite scroll.

Never render thousands of rows.

---

# Realtime Rules

Use Supabase Realtime only for:

* chat
* notifications
* match events

Avoid realtime for everything else.

---

# AI Rules

Use AI only where it creates value.

Examples:

* candidate ranking
* vacancy ranking
* profile improvement
* resume analysis

Do not use AI for:

* authentication
* permissions
* critical business logic

---

# Documentation Rules

Every major feature must include:

* purpose
* database changes
* API changes
* security impact

---

# Testing Rules

Critical features must be tested:

* authentication
* payments
* matches
* messaging

---

# MVP Rules

MVP includes only:

* registration
* login
* profiles
* vacancies
* swipes
* matches
* chat
* notifications

Anything else is out of scope unless explicitly approved.

---

# Solo Founder Rule

The project is maintained by one developer.

Every solution must be:

* cheap
* simple
* maintainable
* scalable

Avoid enterprise-level complexity.

---

# Golden Rule

If two solutions solve the same problem:

Choose the simpler one.
