import asyncio

try:
    import nest_asyncio
except ModuleNotFoundError:
    import os
    os.system("pip install nest_asyncio")
    import nest_asyncio

from telegram.ext import Application, CommandHandler, ContextTypes
from telegram import Update

nest_asyncio.apply()

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Welcome! The bot is working ✅")

TOKEN = "8092491971:AAHPebcXzO0JMjH8Jk0FofD3Zg92TNjPCnE"

async def main():
    app = Application.builder().token(TOKEN).build()
    app.add_handler(CommandHandler("start", start))
    print("Bot is running... open Telegram and send /start")
    await app.run_polling()

loop = asyncio.get_event_loop()
loop.create_task(main())
loop.run_forever()
