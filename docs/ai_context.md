# AI Context

## Project

FastHire

IT recruiting platform based on mutual matching.

Candidates swipe vacancies.

Employers swipe candidates.

When both sides like each other:

* Match is created
* Chat opens
* Interview can be scheduled

---

# Business Goal

Reduce hiring friction.

Reduce time from registration to interview.

Make hiring feel like Tinder.

---

# Target Audience

## Candidates

* Frontend Developer
* Backend Developer
* Fullstack Developer
* QA Engineer
* DevOps Engineer
* Data Engineer
* Data Scientist
* ML Engineer
* Python Developer
* Java Developer
* 1C Developer

---

## Employers

* Startups
* Product companies
* Outsourcing companies
* FinTech companies
* Enterprise companies

---

# Core Principles

## Simplicity

Every action should require minimum clicks.

---

## Mobile First

Primary platform is mobile.

Desktop is secondary.

---

## Fast Matching

Users should start swiping immediately after onboarding.

---

## Realtime

Matches and chat should update instantly.

---

## Security First

Security is more important than development speed.

---

# Technology Stack

Frontend:

* Next.js 15
* TypeScript
* TailwindCSS
* Shadcn UI

Backend:

* Supabase

Database:

* PostgreSQL

Authentication:

* Supabase Auth

Storage:

* Supabase Storage

Realtime:

* Supabase Realtime

Hosting:

* Vercel

Monitoring:

* Sentry

Analytics:

* PostHog

AI:

* OpenAI API

---

# User Roles

## Candidate

Can:

* create profile
* upload resume
* edit profile
* swipe vacancies
* receive matches
* chat

---

## Employer

Can:

* create company
* create vacancies
* swipe candidates
* receive matches
* chat

---

## Moderator

Can:

* review reports
* hide content
* block users

---

## Admin

Can:

* manage moderation
* manage users

---

## SuperAdmin

Can:

* manage platform
* manage subscriptions
* manage billing
* manage settings

---

# MVP Scope

Included:

* registration
* login
* candidate profile
* employer profile
* company profile
* vacancy creation
* candidate swipe
* employer swipe
* match
* chat
* notifications
* resume upload

Not Included:

* video profiles
* video interviews
* AI interviews
* referral program
* marketplace
* agency tools

---

# Future Integrations

* Telegram Bot
* Telegram Login
* Google OAuth
* Yandex OAuth
* GitHub Import
* HH.ru Import
* LinkedIn Import

---

# AI Usage

Allowed:

* profile recommendations
* vacancy recommendations
* resume improvement
* profile completion suggestions

Forbidden:

* authentication
* authorization
* payment decisions
* moderation decisions without human review

---

# Database Rules

Every table must contain:

* id
* created_at
* updated_at

All user data must be protected by RLS.

---

# Security Rules

Always:

* validate inputs
* validate uploads
* check permissions

Prevent:

* XSS
* CSRF
* SQL Injection
* Spam
* Brute Force

---

# Performance Rules

Prefer:

* pagination
* lazy loading
* caching

Avoid:

* N+1 queries
* huge payloads
* unnecessary rerenders

---

# Success Metrics

Candidate:

* registration to first swipe < 2 minutes

Employer:

* vacancy creation < 3 minutes

Business:

* positive retention
* monthly growth
* CAC lower than LTV

---

# Solo Founder Rule

Project is maintained by one developer.

All solutions must be:

* simple
* scalable
* cheap
* maintainable

Avoid enterprise complexity unless absolutely necessary.
