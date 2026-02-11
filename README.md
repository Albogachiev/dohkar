# Предусловия

* Docker Desktop запуще
* Node.js ≥ 20 (для локальных команд, если понадобятся)
* Ты в корне репозитория (где docker-compose.yml)

# Подготовить .env
* cp server/.env.example server/.env
* cp client/.env.example client/.env

# Сгенерировать Prisma client (внутри backend контейнера)
* docker compose exec backend npm run prisma:generate

# Применить миграции (создать таблицы)
* docker compose exec backend npm run prisma:migrate

# Запустить сиды
* docker compose exec backend npm run prisma:seed

# Открыть проект
* Frontend: http://localhost:3000
* Backend: http://localhost:4000

# Поднять инфраструктуру и приложения (dev)
* Без develop.watch, запускаем так:
docker compose up -d --build
* С использованием develop.watch, запускаем так:
docker compose up --watch 


## Если нужно “чистый старт” (стереть БД и поднять заново)
docker compose down -v
docker compose up -d --build
docker compose exec backend npm run prisma:generate
docker compose exec backend npm run prisma:migrate
docker compose exec backend npm run prisma:seed
