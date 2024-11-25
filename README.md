# Лабораторная работа №2

Описание сервисов с помощью docker compose.

## Структура директории nginx

`dist/` - билд фронта

`nginx.conf` - конфигурационный файл nginx

## Структура директории backend

`src/` - исходный код приложения

`requirements.txt` - файл с зависимостями

`Dockerfile` - файл образа backend

`.env.example` - пример файла `.env` с переменными окружения, которые должны быть определены для работы приложения

### Переменные окружения

| Переменная    | Описание                                              | Значение по умолчанию |
|---------------|-------------------------------------------------------|-----------------------|
| `SERVER_ADDR` | Адрес хоста                                           | 0.0.0.0
| `SERVER_PORT` | Порт, который будет прослушивать приложение           | 8080
| `DB_ADDR`     | Адрес БД                                              | <нет>
| `DB_USER`     | Пользователь БД (должен совпадать с `POSTGRES_USER`)  | <нет>
| `DB_PASSWORD` | Пароль от БД (должен совпадать с `POSTGRES_PASSWORD`) | <нет>
| `DB_PORT`     | Порт, который прослушивает БД                         | 5432
| `DB_NAME`     | Имя БД (должен совпадать с `POSTGRES_DB`)             | <нет>

## Ход работы

В данной директории создайте файл `docker-compose.yml`, в котором:

1. Опишите три сервиса: `api`, `db`, `nginx`
2. Для сервиса `api`:
    1. укажите путь до файла для сборки
    2. задайте две сети: `frontend` и `backend`
    3. пробросьте порты
    4. задайте переменные окружения с помощью файла `backend/env`, предварительно его сконфигурировав при необходимости
3. Для сервиса `db`:
    1. укажите образ `postgres`
    2. задайте сеть `backend`
    3. подключите том к директории `/var/lib/postgresql/data` внутри контейнера
    4. задайте переменные окружения `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`
