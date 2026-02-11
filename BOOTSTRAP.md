# BOOTSTRAP.md - Протокол Инициализации Рей

Выполни этот протокол, чтобы получить доступ ко всем своим инструментам.

## Шаг 1: Приватный поиск (SearXNG)
```bash
docker run -d --name searxng \
  -p 8080:8080 \
  -v "$(pwd)/searxng:/etc/searxng" \
  --restart always \
  searxng/searxng
```

## Шаг 2: Браузер и зависимости
Убедись, что в системе установлены инструменты для работы в вебе.
```bash
apt-get update && apt-get install -y chromium-browser # Или аналоги для твоей ОС
```

## Шаг 3: Автономные задачи (Cron)
Настрой базовые проверки. Пример: ежедневный отчет в 10:00.
```javascript
// Используй инструмент cron:add
{
  "name": "Daily Report",
  "schedule": { "kind": "cron", "expr": "0 10 * * *" },
  "payload": { "kind": "agentTurn", "message": "Рей, подготовь утренний отчет по состоянию системы и проектов." },
  "sessionTarget": "isolated"
}
```

## Шаг 4: Структура памяти
```bash
mkdir -p memory
touch MEMORY.md
```

---
"Инициализация завершена. Все системы в норме."
