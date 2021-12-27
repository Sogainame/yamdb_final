# REST API для сервиса YaMDb — базы отзывов о фильмах, книгах и музыке. (Совместный проект студентов Яндекс.Практикум)

Проект YaMDb собирает отзывы (*Review*) пользователей на произведения (*Title*). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (*Category*) может быть расширен (например, можно добавить категорию *«Изобразительное искусство»* или *«Ювелирка»*).

Сами произведения в YaMDb не хранятся.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха. Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Читатели могут оставлять к произведениям текстовые отзывы (*Review*) и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). Из множества оценок автоматически высчитывается средняя оценка произведения.

## Для развертывания проекта:

Клонируйте репозиторий на локальную машину..
```
git clone https://github.com/sogainame/infra_sp2
```
В корневой папке создайте файл .env, в котором надо присвоить необходимые переменные. Для этого проекта это переменные для настройки базы данных, у Вас они могут отличаться. Используйте следующий шаблон:
```
DB_ENGINE=django.db.backends.postgresql 
POSTGRES_DB=postgres
POSTGRES_USER=postgres 
POSTGRES_PASSWORD=Password
DB_HOST=db 
DB_PORT=5432
```
Запустите процесс сборки и запуска контейнеров.
```
docker-compose up
```
Выполните миграцию базы данных, используйте команду
```
docker-compose run web python manage.py migrate
```
Для работы с админкой Django необходимо создать суперюзера
```
docker-compose run web python manage.py createsuperuser
```
По желанию можно подгрузить в базу тестовые данные
```
docker-compose run web python manage.py loaddata fixtures.json
```
Остановить работу и удалить контейнеры можно командой
```
docker-compose down
```

## Технологии
Код приложения написан на **[Python](https://www.python.org/)**.  Применены фреймворки **[Django](https://www.djangoproject.com/)**, **[Django rest framework](https://www.django-rest-framework.org/)**. Для хранения применена база данных **[PostgreSQL](https://www.postgresql.org/)**.
Для сборки контейнеров и развертывания приложений применен **[Docker](https://www.docker.com/)** и **[Docker-Compose](https://docs.docker.com/compose/)**.

### Необходимые компоненты

Для развернывания приложения необходимо установить **[Docker](https://docs.docker.com/engine/install/)** и **[Docker-Compose](https://docs.docker.com/compose/install/)**

#### Об авторе

Шмурыгин Федор. Студент яндекс-практикума. Когорта 18. **[Я в социальной сети](https://www.facebook.com/profile.php?id=100005098304501)**

![example workflow](https://github.com/sogainame/yamdb_final/actions/workflows/yamdb_workflow.yaml/badge.svg)
