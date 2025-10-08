# bot-code
import telebot
import random
import os
print(os.listdir('images'))

bot = telebot.TeleBot('Token Here')

@bot.message_handler(commands=['start'])
def start_command(message):
    bot.send_message(message.chat.id, "Привет! 🙌\nИспользуй команду /help, чтобы узнать, что я умею 💡")

@bot.message_handler(commands=['glass'])
def glass_info(message):
    bot.send_message(message.chat.id, "Стекло можно перерабатывать почти бесконечно! Разделяйте бутылки и банки от мусора и выбрасывайте в специальные контейнеры ♻️")

@bot.message_handler(commands=['paper'])
def send_mem(message):
    img_name = random.choice(os.listdir('images'))
    with open(f'images/{img_name}', 'rb') as f:
        bot.send_photo(message.chat.id, f)

@bot.message_handler(commands=['fact'])
def get_fact(message):
    facts = [
        "Слон — единственное животное, которое не может прыгать 🐘",
        "Мёд никогда не портится 🍯",
        "У осьминога три сердца ❤️❤️❤️",
        "Пингвины делают предложение камнем 💍🐧",
        "Кошки спят около 70% своей жизни 💤",
        "Бананы — ягоды, а клубника — нет 🍌🍓",
        "Утки издают звук, но не эхо 🦆",
        "Дельфины спят с одним открытым глазом 🐬",
        "Крокодилы не могут высовывать язык 🐊",
        "Муравьи не спят 🐜",
        "Летучие мыши всегда поворачивают налево при выходе из пещеры 🦇",
        "Жирафы не умеют кашлять 🦒",
        "Коровы имеют лучших друзей 🐄",
        "Собаки видят мир в оттенках синего и жёлтого 🐕",
        "Пчёлы могут узнавать человеческие лица 🐝"
    ]
    bot.send_message(message.chat.id, random.choice(facts))

# 🧴 Пластик
@bot.message_handler(commands=['plastic'])
def plastic_info(message):
    bot.send_message(message.chat.id, "Пластик сортируйте по типу: бутылки, крышки, пакеты — отдельно. Лучше сдавать их в пункты переработки ♻️")

# 🧲 Металл
@bot.message_handler(commands=['metal'])
def metal_info(message):
    bot.send_message(message.chat.id, "Металлы, такие как алюминиевые банки и крышки, перерабатываются почти бесконечно. Не выбрасывайте их с обычным мусором ⚙️")

# 😂 Шутка
@bot.message_handler(commands=['joke'])
def send_joke(message):
    jokes = [
        "Почему программист не может выбросить мусор? — Он ждёт, когда сборщик мусора запустится автоматически 😄",
        "Учёные доказали: чем меньше уроков, тем счастливее дети 😜",
        "Почему у пчёл хорошие оценки? — Они всегда на своём уровне «B»! 🐝",
        "Компьютер грустит... у него мало оперативки 😢"
    ]
    bot.send_message(message.chat.id, random.choice(jokes))

# 💡 Совет дня
@bot.message_handler(commands=['tip'])
def send_tip(message):
    tips = [
        "Не выбрасывай батарейки в мусор — сдай их на переработку 🔋",
        "Выключай свет, выходя из комнаты 💡",
        "Используй сумку вместо пластиковых пакетов 👜",
        "Сортируй отходы — это просто шаг к чистой планете 🌍"
    ]
    bot.send_message(message.chat.id, random.choice(tips))

# ℹ️ Помощь
@bot.message_handler(commands=['help'])
def help_info(message):
    bot.send_message(message.chat.id,
                     "Вот мои команды:\n"
                     "/start — начало работы\n"
                     "/help — список команд\n"
                     "/paper — случайное изображение\n"
                     "/glass — советы по стеклу\n"
                     "/plastic — советы по пластику\n"
                     "/metal — советы по металлу\n"
                     "/fact — случайный факт\n"
                     "/joke — случайная шутка\n"
                     "/tip — полезный совет")

bot.polling()
