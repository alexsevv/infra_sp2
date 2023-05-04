# REST API YamDB - база отзывов о фильмах, музыке и книгах
## Стек
* Python 3.7.0
* Django 3.2
* DRF 3.12.4
* Nginx
* docker-compose
* gunicorn
* PosrgeSQL

## Описание
Проект позволяет авторизованным пользователям ставить оценки разным произведениям, оставлять комментарии, отзывы к ним.

## Как запустить
Клонировать репозиторий
```
git clone git@github.com:alexsevv/infra_sp2.git
```
В папке infra создайте файл .env и пропишите в нем дефолтные значения:
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```
Перейти в папку infra и запустить docker-compose.yaml (при установленном и запущенном Docker)
```
sudo docker compose up -d --build
```
```
sudo docker compose exec web python manage.py makemigrations # создали миграции
sudo docker compose exec web python manage.py migrate # прогнали миграции
sudo docker compose exec web python manage.py createsuperuser # создали суперюзера
sudo docker compose exec web python manage.py collectstatic --no-input # собрали статику
sudo docker compose exec web python manage.py loaddata fixtures.json # заполнили БД тестовыми данными
```
Проверяем работоспособность приложения:
```
 http://localhost/admin/
```
## Документация к API:
Здесь описаны все доступные ендпоинты и примеры запросов к ним:
http://localhost/redoc/

## Авторы проекта
- [Александр Матияка](https://github.com/alexsevv)
- [Максим Краев](https://github.com/loony-m)
- [Алексей Алексеев](https://github.com/Litandepython)