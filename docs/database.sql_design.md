# Database SQL Design

Версия: 1.0

Цель:

Спроектировать БД таким образом, чтобы MVP можно было быстро реализовать на Supabase и масштабировать без полного рефакторинга.

---

# Общие правила

## UUID

Во всех таблицах использовать UUID.

Не использовать integer id.

Пример:

id uuid primary key default gen_random_uuid()

---

## Временные поля

Во всех таблицах:

created_at timestamptz default now()

updated_at timestamptz default now()

---

## Soft Delete

Удаление записей только логическое.

Поле:

deleted_at timestamptz

---

# Таблица users

Источник:

Supabase Auth

Хранит основные данные пользователя.

```sql
users
```

Поля:

```sql
id uuid primary key

email text unique

role text

is_active boolean

is_banned boolean

created_at timestamptz
updated_at timestamptz
```

---

Допустимые роли:

```text
candidate
employer
moderator
admin
```

---

# Таблица candidate_profiles

Профиль кандидата.

```sql
candidate_profiles
```

Поля:

```sql
id uuid primary key

user_id uuid references users(id)

first_name text

last_name text

city text

country text

about text

experience_years integer

salary_expectation integer

employment_type text

job_search_status text

resume_url text

video_url text

avatar_url text

is_verified boolean

created_at timestamptz
updated_at timestamptz
```

---

job_search_status

```text
active
open
inactive
```

---

# Таблица candidate_skills

Навыки кандидата.

```sql
candidate_skills
```

Поля:

```sql
id uuid primary key

candidate_id uuid references candidate_profiles(id)

skill_name text

years_of_experience integer
```

---

Примеры:

```text
Java
Python
1С
QA
DevOps
React
Node.js
Data Engineering
```

---

# Таблица employer_profiles

Компания.

```sql
employer_profiles
```

Поля:

```sql
id uuid primary key

user_id uuid references users(id)

company_name text

inn text

ogrn text

website text

description text

logo_url text

is_verified boolean

created_at timestamptz
updated_at timestamptz
```

---

# Таблица vacancies

Вакансии.

```sql
vacancies
```

Поля:

```sql
id uuid primary key

employer_id uuid references employer_profiles(id)

title text

description text

salary_from integer

salary_to integer

currency text

experience_level text

employment_type text

location text

is_remote boolean

status text

created_at timestamptz
updated_at timestamptz
```

---

status

```text
draft
active
archived
closed
```

---

experience_level

```text
junior
middle
senior
lead
```

---

# Таблица vacancy_skills

Стек вакансии.

```sql
vacancy_skills
```

Поля:

```sql
id uuid primary key

vacancy_id uuid references vacancies(id)

skill_name text
```

---

# Таблица swipes

История свайпов.

```sql
swipes
```

Поля:

```sql
id uuid primary key

candidate_id uuid references candidate_profiles(id)

vacancy_id uuid references vacancies(id)

direction text

created_at timestamptz
```

---

direction

```text
like
pass
```

---

Уникальность:

```sql
candidate_id + vacancy_id
```

---

# Таблица employer_candidate_swipes

Свайпы работодателя.

```sql
employer_candidate_swipes
```

Поля:

```sql
id uuid primary key

employer_id uuid references employer_profiles(id)

candidate_id uuid references candidate_profiles(id)

direction text

created_at timestamptz
```

---

# Таблица matches

Совпадения.

```sql
matches
```

Поля:

```sql
id uuid primary key

candidate_id uuid references candidate_profiles(id)

vacancy_id uuid references vacancies(id)

employer_id uuid references employer_profiles(id)

created_at timestamptz
```

---

Уникальность:

```sql
candidate_id + vacancy_id
```

---

# Таблица chats

Чат после матча.

```sql
chats
```

Поля:

```sql
id uuid primary key

match_id uuid references matches(id)

created_at timestamptz
```

---

# Таблица messages

Сообщения.

```sql
messages
```

Поля:

```sql
id uuid primary key

chat_id uuid references chats(id)

sender_user_id uuid references users(id)

message text

is_read boolean

created_at timestamptz
```

---

# Таблица reports

Жалобы.

```sql
reports
```

Поля:

```sql
id uuid primary key

reporter_user_id uuid references users(id)

target_user_id uuid references users(id)

reason text

description text

status text

created_at timestamptz
```

---

status

```text
new
reviewing
resolved
rejected
```

---

# Таблица subscriptions

Подписки работодателей.

```sql
subscriptions
```

Поля:

```sql
id uuid primary key

employer_id uuid references employer_profiles(id)

plan text

status text

started_at timestamptz

expires_at timestamptz
```

---

plan

```text
free
pro
business
enterprise
```

---

# Таблица audit_logs

Журнал безопасности.

```sql
audit_logs
```

Поля:

```sql
id uuid primary key

user_id uuid

action text

entity_type text

entity_id uuid

ip_address text

user_agent text

created_at timestamptz
```

---

# Индексы

Создать индексы:

```sql
candidate_profiles(user_id)

candidate_skills(skill_name)

vacancies(status)

vacancies(is_remote)

vacancies(created_at)

vacancy_skills(skill_name)

swipes(candidate_id)

swipes(vacancy_id)

matches(candidate_id)

matches(employer_id)

messages(chat_id)

messages(created_at)

reports(status)
```

---

# Full Text Search

Для вакансий:

```sql
title

description
```

---

Для кандидатов:

```sql
about

skills
```

---

# Масштабирование

До 10 000 пользователей:

одна база.

---

До 100 000 пользователей:

read replicas.

---

Свыше 1 млн пользователей:

разделение:

* auth
* search
* analytics

в отдельные сервисы.

---

# Запрещено

Нельзя хранить:

* пароли
* токены
* данные банковских карт

Все это должно храниться только через внешние сервисы.

---

# Готовность MVP

База считается готовой если:

* все таблицы созданы
* индексы созданы
* RLS настроен
* аудит включен
* бэкапы включены
* realtime работает для чатов
