# Architecture

Frontend:
- Next.js

Backend:
- Supabase

Database:
- PostgreSQL

Auth:
- Supabase Auth

Storage:
- Supabase Storage

Realtime:
- Supabase Realtime

AI:
- OpenAI API

Hosting:
- Vercel

Monitoring:
- Sentry

Analytics:
- PostHog
## Core Entities

### User
Общий пользователь системы

Типы:
- candidate
- employer
- admin

### CandidateProfile

Поля:
- имя
- фото
- стек технологий
- опыт
- зарплатные ожидания
- локация
- резюме
- видео визитка

### EmployerProfile

Поля:
- название компании
- описание
- логотип
- сайт

### Vacancy

Поля:
- название
- описание
- зарплата
- стек
- формат работы
- статус

### Swipe

Лайк или пропуск

Тип:
- like
- pass

### Match

Взаимный лайк

### Chat

Чат после матча

### Message

Сообщение в чате

### Report

Жалоба

### Subscription

Подписка работодателя
