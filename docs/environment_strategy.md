# Environment Strategy

## Environments

### Local

Для разработки.

### Staging

Для тестирования перед релизом.

### Production

Боевой сервер.

---

## Supabase Projects

### Local

Локальный Supabase.

### Staging

Отдельный проект.

### Production

Отдельный проект.

---

## Vercel Projects

### Preview

Автоматически из Pull Request.

### Production

Основной сайт.

---

## Rules

Никогда не тестировать новые функции на Production.

Никогда не использовать Production базу для разработки.

Все изменения сначала проходят через Local → Staging → Production.
