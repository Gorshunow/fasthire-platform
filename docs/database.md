# Database

## Database Engine

PostgreSQL

Provider:

Supabase

---

# Main Principles

Каждая сущность имеет:

* id (UUID)
* created_at
* updated_at

Все связи строятся через UUID.

Удаление данных через soft delete.

Поле:

deleted_at

---

# Tables

## profiles

Основная таблица пользователей.

Связана с auth.users.

### Fields

id UUID PK

email TEXT

role TEXT

Варианты:

* candidate
* employer
* moderator
* admin

telegram_username TEXT

avatar_url TEXT

is_active BOOLEAN

is_verified BOOLEAN

created_at TIMESTAMP

updated_at TIMESTAMP

deleted_at TIMESTAMP

---

# candidate_profiles

Профиль кандидата.

### Fields

id UUID PK

user_id UUID FK -> profiles.id

first_name TEXT

last_name TEXT

city TEXT

country TEXT

headline TEXT

about TEXT

experience_years INTEGER

salary_expectation INTEGER

currency TEXT

employment_type TEXT

resume_url TEXT

video_url TEXT

english_level TEXT

linkedin_url TEXT

github_url TEXT

portfolio_url TEXT

created_at TIMESTAMP

updated_at TIMESTAMP

---

# employer_profiles

Профиль работодателя.

### Fields

id UUID PK

user_id UUID FK -> profiles.id

company_name TEXT

company_description TEXT

website TEXT

logo_url TEXT

company_size INTEGER

country TEXT

city TEXT

created_at TIMESTAMP

updated_at TIMESTAMP

---

# technologies

Справочник технологий.

### Fields

id UUID PK

name TEXT

slug TEXT

category TEXT

created_at TIMESTAMP

---

Примеры:

* 1C
* Java
* Python
* QA
* DevOps
* React
* Vue
* Angular
* PostgreSQL
* Docker

---

# candidate_technologies

Связь кандидат ↔ технология.

### Fields

id UUID PK

candidate_id UUID

technology_id UUID

level TEXT

Варианты:

* junior
* middle
* senior
* lead

created_at TIMESTAMP

---

# vacancies

Вакансии.

### Fields

id UUID PK

employer_id UUID

title TEXT

description TEXT

salary_from INTEGER

salary_to INTEGER

currency TEXT

experience_required INTEGER

employment_type TEXT

work_format TEXT

city TEXT

country TEXT

status TEXT

Варианты:

* draft
* active
* paused
* archived

created_at TIMESTAMP

updated_at TIMESTAMP

---

# vacancy_technologies

Связь вакансия ↔ технология.

### Fields

id UUID PK

vacancy_id UUID

technology_id UUID

required BOOLEAN

created_at TIMESTAMP

---

# candidate_swipes

Свайпы кандидатов.

### Fields

id UUID PK

candidate_id UUID

vacancy_id UUID

action TEXT

Варианты:

* like
* pass

created_at TIMESTAMP

---

# employer_swipes

Свайпы работодателей.

### Fields

id UUID PK

employer_id UUID

candidate_id UUID

action TEXT

Варианты:

* like
* pass

created_at TIMESTAMP

---

# matches

Взаимные лайки.

### Fields

id UUID PK

candidate_id UUID

employer_id UUID

vacancy_id UUID

match_score INTEGER

status TEXT

Варианты:

* active
* closed

created_at TIMESTAMP

---

# chats

Чаты.

### Fields

id UUID PK

match_id UUID

created_at TIMESTAMP

---

# messages

Сообщения.

### Fields

id UUID PK

chat_id UUID

sender_id UUID

message TEXT

message_type TEXT

Варианты:

* text
* image
* file

created_at TIMESTAMP

---

# reports

Жалобы.

### Fields

id UUID PK

reporter_id UUID

reported_user_id UUID

reason TEXT

status TEXT

Варианты:

* open
* reviewed
* closed

created_at TIMESTAMP

---

# subscriptions

Подписки работодателей.

### Fields

id UUID PK

employer_id UUID

plan TEXT

Варианты:

* free
* pro
* business

status TEXT

Варианты:

* active
* cancelled
* expired

started_at TIMESTAMP

expires_at TIMESTAMP

created_at TIMESTAMP

---

# payments

История платежей.

### Fields

id UUID PK

subscription_id UUID

provider TEXT

amount INTEGER

currency TEXT

status TEXT

transaction_id TEXT

created_at TIMESTAMP

---

# notifications

Уведомления.

### Fields

id UUID PK

user_id UUID

type TEXT

title TEXT

body TEXT

is_read BOOLEAN

created_at TIMESTAMP

---

# audit_logs

Журнал действий.

Используется для безопасности.

### Fields

id UUID PK

user_id UUID

action TEXT

entity_type TEXT

entity_id UUID

ip_address TEXT

user_agent TEXT

created_at TIMESTAMP

---

# user_consents

Согласия пользователя.

Требование законодательства РФ.

### Fields

id UUID PK

user_id UUID

consent_type TEXT

accepted BOOLEAN

accepted_at TIMESTAMP

ip_address TEXT

created_at TIMESTAMP

---

Типы согласий:

* privacy_policy
* terms_of_service
* personal_data_processing
* marketing_emails

---

# Security

Использовать RLS для всех таблиц.

Пользователь должен видеть только свои данные.

Работодатель должен видеть только свои вакансии.

Модератор видит всё.

Администратор видит всё.

---

# Storage Buckets

avatars

Хранение аватаров.

---

resumes

PDF резюме.

---

videos

Видео визитки.

---

company-logos

Логотипы компаний.

---

chat-files

Файлы чатов.

---

# Future Tables

Будут добавлены позже.

## ai_match_results

Результаты AI анализа.

---

## interviews

AI интервью.

---

## interview_answers

Ответы кандидатов.

---

## recruiter_profiles

Рекрутеры.

---

## recruiter_commissions

Комиссии рекрутеров.

---

# Important

Не создавать дополнительные таблицы до появления реальной потребности.

Сначала пользователи.

Потом усложнение архитектуры.
