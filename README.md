```bash
effective-mobile/
├── backend/
│ ├── Dockerfile
│ └── app.py
├── nginx/
│ └── nginx.conf
├── docker-compose.yml
└── README.md
```

## Как запустить

1. Клонируйте репозиторий

```bash
git clone git@github.com:Vulpe-Cult/effective-mobile.git
cd effective-mobile
```


2. Запустите контейнеры

```bash
docker compose up -d --build
```
```bash
Как устроено

backend -простой HTTP-сервер на модуле http.server
Слушает порт 8080 только внутри Docker-сети
Отвечает текстом на GET /
nginx -reverse proxy
Принимает запросы на порт 80 хоста
Проксирует все запросы на http://backend:8080/
Конфигурация полностью переопределяет дефолтную (через command в compose)
Сеть -bridge-сеть internal
Контейнеры общаются друг с другом по имени сервиса (backend)
```



