# FastHire Architecture

## Project Goal

FastHire — платформа поиска работы для IT-специалистов в формате Tinder.

Кандидаты свайпают вакансии.
Работодатели свайпают кандидатов.

При взаимном интересе создаётся Match и открывается чат.

---

# Technology Stack

## Frontend

* Next.js 15
* TypeScript
* Tailwind CSS
* Shadcn UI
* React Hook Form
* Zod

Причины выбора:

* быстро
* бесплатно
* SEO
* легко развивать
* отлично подходит для AI-кодинга

---

## Backend

* Supabase

Используется для:

* PostgreSQL
* Auth
* Storage
* Realtime
* Edge Functions

Причины:

* максимально дешево
* минимум DevOps
* быстро разрабатывать одному

---

## Database

* PostgreSQL

Особенности:

* Row Level Security (RLS)
* Full Text Search
* Индексы для масштабирования

---

## Authentication

* Supabase Auth

Методы входа:

* Email + Password
* Telegram Login (этап 2)

Дополнительно:

* Email Verification
* Password Reset
* Session Management

---

## Storage

* Supabase Storage

Хранение:

* фото профиля
* логотипы компаний
* резюме PDF
* видео визитки

---

## Realtime

* Supabase Realtime

Используется для:

* чатов
* уведомлений
* матчей

---

## AI Layer

* OpenAI API

Функции:

* анализ резюме
* рекомендации вакансий
* рекомендации кандидатов
* генерация описаний вакансий
* AI-помощник HR

---

## Hosting

Frontend:

* Vercel

Backend:

* Supabase Cloud

---

## Monitoring

### Sentry

Отслеживание:

* ошибок frontend
* ошибок backend
* производительности

### PostHog

Отслеживание:

* регистраций
* конверсий
* поведения пользователей
* воронки продаж

---

# Security Architecture

## Обязательные меры

### Row Level Security

Все таблицы работают через RLS.

Пользователь может видеть только свои данные.

---

### Rate Limiting

Защита от:

* спама
* ботов
* DDoS

Ограничения:

* логин
* регистрация
* чат
* лайки
* загрузка файлов

---

### Input Validation

Используем:

* Zod
* Server Validation

Проверяется каждый запрос.

---

### File Protection

Разрешенные форматы:

* jpg
* jpeg
* png
* pdf
* mp4

Проверяются:

* размер
* MIME тип
* расширение

---

### Secrets

Никогда не храним:

* API ключи в коде
* пароли в репозитории

Используем:

* Environment Variables

---

# Russian Compliance

## Персональные данные

Учитываем требования:

* 152-ФЗ
* Политика конфиденциальности
* Пользовательское соглашение

---

## Согласия

Пользователь подтверждает:

* согласие на обработку данных
* согласие на хранение резюме

---

## Удаление данных

Пользователь может:

* удалить аккаунт
* удалить резюме
* удалить профиль

---

# User Roles

## Candidate

Может:

* создавать профиль
* загружать резюме
* свайпать вакансии
* общаться в чате

---

## Employer

Может:

* создавать компанию
* публиковать вакансии
* свайпать кандидатов
* общаться в чате

---

## Moderator

Может:

* обрабатывать жалобы
* скрывать вакансии
* блокировать пользователей

---

## Admin

Полный доступ к системе.

---

# Core Entities

## User

Общий пользователь системы.

Типы:

* candidate
* employer
* moderator
* admin

---

## CandidateProfile

Поля:

* first_name
* last_name
* avatar_url
* city
* country
* skills
* experience_years
* expected_salary
* resume_url
* video_url
* about

---

## EmployerProfile

Поля:

* company_name
* logo_url
* website
* description
* company_size

---

## Vacancy

Поля:

* title
* description
* salary_from
* salary_to
* technologies
* work_format
* location
* status

---

## Swipe

Поля:

* user_id
* target_id
* action

action:

* like
* pass

---

## Match

Поля:

* candidate_id
* employer_id
* vacancy_id
* created_at

---

## Chat

Поля:

* match_id

---

## Message

Поля:

* chat_id
* sender_id
* text

---

## Report

Поля:

* reporter_id
* target_id
* reason

---

## Subscription

Поля:

* employer_id
* plan
* status
* expires_at

---

# Future Architecture

После достижения:

* 10 000 пользователей

Добавляем:

* Redis
* Queue System
* Background Jobs

После достижения:

* 100 000 пользователей

Добавляем:

* отдельный Backend API
* CDN
* Search Engine

При этом текущая архитектура не требует полного переписывания проекта.
