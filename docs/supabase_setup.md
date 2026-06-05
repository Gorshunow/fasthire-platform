# Supabase Setup

## Purpose

This document describes how to create and configure the FastHire backend infrastructure.

Goal:

* production-ready setup
* minimal cost
* maximum scalability
* security by default

---

# Step 1. Create Supabase Account

Open:

https://supabase.com

Register using:

* Email
  or
* GitHub

Recommended:

Use GitHub login.

---

# Step 2. Create Project

Click:

New Project

Project Name:

FastHire

Database Password:

Generate strong password.

Store password in password manager.

Region:

Choose closest region to most users.

Recommended:

Frankfurt

Reason:

* good latency
* stable
* GDPR compliant

---

# Step 3. Save Credentials

After project creation save:

Project URL

Example:

https://xxxxx.supabase.co

---

Anon Key

Example:

public key

---

Service Role Key

IMPORTANT:

Never expose publicly.

Never store in frontend.

Only backend usage.

---

# Step 4. Enable Authentication

Open:

Authentication

Enable:

* Email Login

Disable:

* Phone Login

for MVP

---

# Step 5. Email Confirmation

Enable:

Email Confirmation

Required:

YES

Reason:

Reduce spam accounts.

---

# Step 6. Password Policy

Minimum:

8 characters

Recommended:

12+

Require:

* uppercase
* lowercase
* number

---

# Step 7. Configure Auth Providers

MVP:

Enable only:

Email

Future:

* Google
* GitHub
* Telegram
* Yandex

---

# Step 8. Configure Storage

Create bucket:

resumes

Private:

YES

Allowed files:

* pdf
* doc
* docx

Max Size:

10 MB

---

Create bucket:

avatars

Public:

YES

Allowed:

* png
* jpg
* jpeg
* webp

Max Size:

5 MB

---

# Step 9. Configure Realtime

Enable:

Realtime

Required tables later:

* matches
* messages
* notifications

---

# Step 10. Database Extensions

Open:

SQL Editor

Run:

create extension if not exists pgcrypto;

create extension if not exists pg_trgm;

create extension if not exists unaccent;

Purpose:

pgcrypto

UUID generation

pg_trgm

search optimization

unaccent

search without accent sensitivity

---

# Step 11. Enable Row Level Security

Rule:

Every table must have RLS enabled.

No exceptions.

---

# Step 12. Configure Backups

Free Plan:

automatic Supabase backups

Paid Plan:

daily backups

recommended later

---

# Step 13. Configure Rate Limits

Authentication:

Enable default Supabase protections.

Additional rate limiting will be implemented in application layer.

Protect:

* login
* registration
* password reset

---

# Step 14. Environment Variables

Create:

.env.local

Example:

NEXT_PUBLIC_SUPABASE_URL=

NEXT_PUBLIC_SUPABASE_ANON_KEY=

SUPABASE_SERVICE_ROLE_KEY=

OPENAI_API_KEY=

POSTHOG_KEY=

SENTRY_DSN=

Never commit this file.

---

# Step 15. Configure Git Ignore

Ensure:

.env.local

exists inside:

.gitignore

---

# Step 16. Enable Audit Logging

Recommended:

Store:

* user bans
* moderation actions
* admin actions

Future table:

audit_logs

---

# Step 17. Security Checklist

Before production:

* RLS enabled
* storage secured
* email confirmation enabled
* service key hidden
* environment variables configured
* rate limiting configured

---

# Expected Cost

MVP Stage

Supabase Free

Cost:

0$

Expected capacity:

* several thousand users
* thousands of resumes
* thousands of matches

---

# Upgrade Trigger

Upgrade to paid plan only when:

* storage becomes limiting
  or
* database size becomes limiting
  or
* active users exceed free tier limits

Until then:

Stay on free plan.

---

# Success Criteria

Project is ready when:

* Supabase project created
* Auth enabled
* Storage buckets created
* Extensions installed
* Environment variables saved
* Security checklist completed

Then database schema creation can begin.
