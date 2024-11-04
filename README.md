- 👋 Hi, I’m @UznevlN1
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
UznevlN1/UznevlN1 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->Telegram uchun kino bot yaratishda foydalanish mumkin bo'lgan oddiy Python kodini aiogram yordamida tuzib beraman. Bu bot foydalanuvchilarga kino nomini qidirish va ma'lumot olish imkoniyatini beradi.

Kerakli kutubxonalarni o'rnating:

pip install aiogram requests

Kod namunasi:

from aiogram import Bot, Dispatcher, types
from aiogram.utils import executor
import requests
import os

API_TOKEN = 'YOUR_TELEGRAM_BOT_TOKEN'
MOVIE_API_URL = 'https://api.example.com/movies?query='  # Kino ma'lumotlari uchun API URL
MOVIE_API_KEY = 'YOUR_MOVIE_API_KEY'

bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)

@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
    await message.reply("Salom! Kino qidirish uchun kino nomini kiriting.")

@dp.message_handler()
async def search_movie(message: types.Message):
    query = message.text
    response = requests.get(f"{MOVIE_API_URL}{query}&api_key={MOVIE_API_KEY}")
    
    if response.status_code == 200:
        movie_data = response.json()
        if movie_data['results']:
            movie = movie_data['results'][0]
            title = movie['title']
            overview = movie['overview']
            release_date = movie['release

Telegram uchun kino bot yaratishda foydalanish mumkin bo'lgan oddiy Python kodini aiogram yordamida tuzib beraman. Bu bot foydalanuvchilarga kino nomini qidirish va ma'lumot olish imkoniyatini beradi.

Kerakli kutubxonalarni o'rnating:

pip install aiogram requests

Kod namunasi:

from aiogram import Bot, Dispatcher, types
from aiogram.utils import executor
import requests
import os

API_TOKEN = 'YOUR_TELEGRAM_BOT_TOKEN'
MOVIE_API_URL = 'https://api.example.com/movies?query='  # Kino ma'lumotlari uchun API URL
MOVIE_API_KEY = 'YOUR_MOVIE_API_KEY'

bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)

@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
    await message.reply("Salom! Kino qidirish uchun kino nomini kiriting.")

@dp.message_handler()
async def search_movie(message: types.Message):
    query = message.text
    response = requests.get(f"{MOVIE_API_URL}{query}&api_key={MOVIE_API_KEY}")
    
    if response.status_code == 200:
        movie_data = response.json()
        if movie_data['results']:
            movie = movie_data['results'][0]
            title = movie['title']
            overview = movie['overview']
            release_date = movie['release_date']
            reply = f"Kino: {title}\nChiqarilgan sana: {release_date}\nTavsif: {overview}"
        else:
            reply = "Kino topilmadi. Boshqa nomni sinab ko'ring."
    else:
        reply = "Kino ma'lumotlarini olishda xatolik yuz berdi."
    
    await message.reply(reply)

if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)

Qadamlar:

1. API tokenni almashtirish: YOUR_TELEGRAM_BOT_TOKEN o'rniga BotFather orqali olingan bot tokenni qo'ying.


2. Kino API URL va kalit: Kino ma'lumotlari uchun MOVIE_API_URL va YOUR_MOVIE_API_KEY ni kino ma'lumotlari beruvchi biror xizmatdan oling (masalan, TMDB API yoki boshqa xizmatlardan).


3. Botni ishga tushirish: Kodni ishga tushirib, Telegram orqali bot bilan muloqot qiling.



Agar boshqa maxsus talablaringiz bo'lsa, kodni moslashtirish mumkin.


