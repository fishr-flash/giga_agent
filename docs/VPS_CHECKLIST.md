# 🚀 Чек-лист по работе с VPS (ForNex) и проектом `giga_agent`

## 1. Подключение к серверу
```bash
ssh giga_ag_fork@<IP_сервера>
```

## 2. Рабочая директория проекта
```bash
cd ~/apps/giga_agent
```

## 3. Основные команды Docker Compose
- Запуск контейнеров:
  ```bash
  docker compose up -d
  ```
- Остановка:
  ```bash
  docker compose down
  ```
- Просмотр статуса:
  ```bash
  docker ps
  ```
- Логи (пример для API):
  ```bash
  docker logs -f giga_agent-langgraph-api-1
  ```

## 4. Сборка образа LangGraph
⚡ Выполняется только при изменениях графа/после клонирования.
```bash
make init_files
make build_graph
```

## 5. Доступ к сервисам
- Фронтенд: `http://<IP_сервера>:8502`
- API LangGraph: доступен внутри контейнеров (`giga_agent-langgraph-api-1`).
- Redis/Postgres: используются только внутри Docker-сети.

## 6. Полезное
- Перезагрузить VPS:
  ```bash
  sudo reboot
  ```
- Проверить healthz вручную:
  ```bash
  curl http://localhost:8502/healthz
  ```

---

> 💡 На будущее: для HTTPS — поставить Nginx + Certbot и завернуть порт `8502` в домен.
