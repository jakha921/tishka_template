Этот темплейт используется для разработки Telegram ботов с использованием библиотеки ['aiogram v3. 0+`](https://github.com/aiogram/aiogram/tree/dev-3.x).

### Для того, чтобы начать использовать:
1. Скопируйте `.env.dist 'в'.env ' и заполните необходимые данные.
2. Создайте новые хэндлеры.
3. **Docker:**
1. Можете сразу запускать проект с Docker, а если у вас его нет, то [скачайте и установите](https://docs.docker.com/get-docker/).
2. Запустите проект с команды `docker-compose up`
4. **Без Docker:**
1. Создайте [venv](https://docs.python.org/3/library/venv.html)
2. Установит зависимости с requirements.txt: `pip install -r requirements.txt`
3. Запустите проект с команды `python3 bot.py`


### Как делать и регистрировать хендлеры:
Создаете модуль `you_name.py` в папке `handlers`.

Создаете роутер в `you_name.py`.
```python
from aiogram import Router
user_router = Router()
```
Можно делать несколько роутеров в одном модуле, и на каждый из них навешивать хэндлеры.
Можно регистрировать хендлеры декораторами:
```python
@user_router.message(commands=["start"])
async def user_start(message):
await message.reply ("Привет, обычный пользователь!")
```

Заходим в файл `bot.py` и добавляем все роутеры в него:
```python
from tgbot.handlers.admin import admin_router
from tgbot.handlers.echo import echo_router
from tgbot.handlers.user import user_router

...

async def main():

...

for router in [
admin_router,
user_router,
...,
echo_router,

]:
dp.include_router(router)
```

### Туториалы с aiogram v3
Відосів пока что нет, но @Groosha уже начал делать [свой учебник](https://groosha.2038.io/telegram-tutorial-2/).
