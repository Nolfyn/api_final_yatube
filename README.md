# <h1 align="center">API для Yatube</h1>
Реализация API для блог-платформы Yatube, на которой пользователи могут создавать посты и оставлять комментарии к ним, а также подписываться на других пользователей. Доступны операции CRUD, используются ViewSet и аутентификация при помощи JWT-токенов.

## Основные технологии
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)
![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)

## Как запустить проект
Клонировать репозиторий и перейти в него в командной строке:

`git clone https://github.com/Nolfyn/api_final_yatube.git`
`cd api_final_yatube`

Cоздать и активировать виртуальное окружение:

`python3 -m venv env`
`source env/bin/activate`

Установить зависимости из файла requirements.txt:

`python3 -m pip install --upgrade pip`
`pip install -r requirements.txt`

Выполнить миграции:

`python3 manage.py migrate`

Запустить проект:

`python3 manage.py runserver`

## Примеры запросов
Пример POST-запроса с токеном Антона Чехова: добавление нового поста.

_POST .../api/v1/posts/_

```
{
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре. Проект Шехтеля всем нравится.",
    "group": 1
} 
```

Пример ответа:

```
{
    "id": 14,
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре. Проект Шехтеля всем нравится.",
    "author": "anton",
    "image": null,
    "group": 1,
    "pub_date": "2021-06-01T08:47:11.084589Z"
} 
```

Пример POST-запроса с токеном Антона Чехова: отправляем новый комментарий к посту с id=14.

_POST .../api/v1/posts/14/comments/_

```
{
    "text": "тест тест"
} 
```

Пример ответа:

```
{
    "id": 4,
    "author": "anton",
    "post": 14,
    "text": "тест тест",
    "created": "2021-06-01T10:14:51.388932Z"
} 
```
