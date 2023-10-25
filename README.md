from aiogram import Bot, Dispatcher, types
from aiogram.utils import executor
from Telegram import kb_client

API_TOKEN = 'Your Token'
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)


@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
    name = message.from_user.first_name
    await message.reply(f"Hello", reply_markup=kb_client)


@dp.message_handler(commands=['help'])
async def send_help(message: types.Message):
    await message.reply("Qanday jardem kerek?")


if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
