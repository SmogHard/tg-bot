# Личный Telegram-бот

Минимальный шаблон для личного Telegram-бота на Python + python-telegram-bot + Docker Compose.

## 1. Получить токен

Зарегистрируй бота через [@BotFather](https://t.me/BotFather) и получи `BOT_TOKEN`.

## 2. Клонировать и запустить

На сервере/компьютере с Docker и Git:

```bash
git clone https://github.com/ТВОЙ_НИК/ИМЯ-РЕПОЗИТОРИЯ.git
cd ИМЯ-РЕПОЗИТОРИЯ
copy .env.example .env  # Windows (cmd)
# или cp .env.example .env в PowerShell/bash
```

Открой `.env` в любом редакторе и замени `BOT_TOKEN` на свой.

Дальше:

```bash
docker compose up -d --build
```

Всё. Бот запустится и будет работать в фоне.

## Управление

- Остановить: `docker compose down`
- Перезапустить: `docker compose restart`
- Логи в реальном времени: `docker compose logs -f`
- Обновить после изменений: `git pull && docker compose up -d --build`

## Добавление команд

Правь `bot.py`. Добавь новый `CommandHandler`, например:

```python
async def ping(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("pong")

app.add_handler(CommandHandler("ping", ping))
```

После правок пересобери:

```bash
docker compose up -d --build
```
