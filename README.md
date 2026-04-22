# 🐱 Kittygram

## 📌 Описание проекта

**Kittygram** — это веб-приложение для публикации информации о котиках.  
Пользователи могут создавать профили своих питомцев, добавлять фотографии, указывать достижения и делиться ими с другими.

Проект реализован как полноценное клиент-серверное приложение с разделением на backend, frontend и nginx-шлюз, развёрнутых в Docker-контейнерах.

---

## 🎯 Цели проекта

- Практика разработки fullstack-приложения
- Освоение Docker и контейнеризации
- Настройка CI/CD через GitHub Actions
- Работа с PostgreSQL и Django REST API
- Разделение frontend и backend

---

## 🚀 Основные функции

- Регистрация и авторизация пользователей
- Создание, редактирование и удаление котиков
- Загрузка изображений
- Добавление достижений питомцам
- REST API для взаимодействия frontend и backend
- Админ-панель Django
- CI/CD: автоматическая проверка, сборка и отправка Docker-образов

---

## 🛠️ Технологический стек

### Backend:
- Python 3.10
- Django
- Django REST Framework
- PostgreSQL
- Gunicorn

### Frontend:
- React
- Node.js

### Инфраструктура:
- Docker
- Docker Compose
- Nginx

### CI/CD:
- GitHub Actions
- Docker Hub

---

## ⚙️ Как развернуть проект

### 1. Клонировать репозиторий

```bash
git clone https://github.com/GoJIub/kittygram_final.git
cd kittygram_final
```

### 2. Создать файл .env

В корне проекта создать файл .env:

```env
# Django
SECRET_KEY=your-secret-key
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1

# PostgreSQL
POSTGRES_DB=kittygram_db
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
POSTGRES_HOST=db
POSTGRES_PORT=5432
```

### 3. Запустить проект

```bash
docker-compose up --build
```

### 4. Применить миграции (если не настроено автоматически)

```bash
docker-compose exec backend python manage.py migrate
```

### 5. Собрать статику

```bash
docker-compose exec backend python manage.py collectstatic --noinput
```

## 🌐 Доступ к приложению

- Приложение: http://localhost:9000
- Админка: http://localhost:9000/admin
- API: http://localhost:9000/api

## 🧪 CI/CD

При каждом пуше в ветку main:

- запускаются тесты backend и frontend
- собираются Docker-образы
- образы отправляются в Docker Hub

## 📦 Структура проекта

```
kittygram_final/
 ├── backend/      # Django API
 ├── frontend/     # React приложение
 ├── nginx/        # Конфигурация nginx
 ├── docker-compose.yml
 └── .github/workflows/
```

## 📌 Примечания
Для корректной работы убедитесь, что Docker установлен и запущен
При изменении .env требуется перезапуск контейнеров
В production рекомендуется использовать HTTPS и настроить домен