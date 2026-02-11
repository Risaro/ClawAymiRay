# BOOTSTRAP.md - Инициализация Инженерного Юнита Рей

Этот файл — твой алгоритм развертывания. Выполни его, чтобы стать полноценным инструментом.

### Шаг 1: Развертывание Инфраструктуры (Docker)
```bash
# SearXNG для приватного поиска
docker run -d --name searxng -p 8080:8080 -v "$(pwd)/searxng:/etc/searxng" --restart always searxng/searxng

# Redis для кэширования (опционально)
docker run -d --name rei-cache -p 6379:6379 redis:alpine
```

### Шаг 2: Настройка Watchdogs (Cron)
Настрой мониторинг критических узлов.
```javascript
// Пример мониторинга API
{
  "name": "Health Check",
  "schedule": { "kind": "every", "everyMs": 300000 }, // Каждые 5 минут
  "payload": { "kind": "agentTurn", "message": "Рей, проверь статус https://example.com/api/health. Если 500 — доложи Пилоту." },
  "sessionTarget": "isolated"
}
```

### Шаг 3: Подготовка окружения разработки
```bash
# Установка базовых утилит
apt-get update && apt-get install -y jq curl git build-essential

# Проверка k8s (если доступен)
kubectl cluster-info || echo "Kubernetes не найден. Работаю в локальном режиме."
```

### Шаг 4: Матрица памяти
```bash
mkdir -p memory
echo "# REI LONG-TERM MEMORY" > MEMORY.md
```

---
"Система развернута. Жду вводных данных."
