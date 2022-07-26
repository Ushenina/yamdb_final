Описание    
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»). Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха. Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»).

Новые жанры может создавать только администратор.

Благодарные или возмущённые читатели оставляют к произведениям текстовые отзывы (Review) и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). Из множества оценок автоматически высчитывается средняя оценка произведения.


[Пример развернутого проекта](http://ushenina.hopto.org/api/v1/)

Установка на локальном компьютере
Приведенная ниже последовательность позволит развернуть проект на локальной машине для тестирования

Установка Docker
Для запуска проекта необходима установка программ docker и docker-compose. https://docs.docker.com/engine/install/

Запуск проекта (Lunux)
Создайте на локальном ПК папку проекта infra_sp2 командой mkdir infra_sp2

Склонируйте репозиторий в текущую папку командой git clone https://github.com/ushenina/infra_sp2/ . и перейдите в нее командой cd infra_sp2

Создайте файл .env командой touch .env с переменными окружениями для работы с базой данных на основе шаблона для работы с базой данных:

DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД 

3.Запустите docker-compose командой sudo docker-compose up -d

Создайте миграции sudo docker-compose exec web python manage.py migrate

Соберите статику проекта командой sudo docker-compose exec web python manage.py collectstatic --no-input

4.Создайте суперпользователя Django sudo docker-compose exec web python manage.py createsuperuser

5.Загрузите фикстуры (тестовые данные) в базу данных командой sudo docker -compose exec web python manage.py loaddata fixtures.json

После описанных выше действий проект будет доступен по адресу http://127.0.0.1

Использованные технологии
Django Rest Framework https://www.django-rest-framework.org/
Django https://www.djangoproject.com/
PostgreSQL https://www.postgresql.org/
Docker https://www.docker.com/

[workflow](https://github.com/ushenina/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Автор проекта
Юлия Ушенина - Python Developer