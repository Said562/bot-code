# bot-code
import telebot
import random
import os
print(os.listdir('images'))

bot = telebot.TeleBot('Token Here')

@bot.message_handler(commands=['start'])
def start_command(message):
    bot.send_message(message.chat.id, "Привет! Используй команду /paper /glass, чтобы получить мем!")

@bot.message_handler(commands=['glass'])
def start_command(message):
    bot.send_message(message.chat.id, "поместите его (бутылки, банки) в синие или зеленые контейнеры для вторсырья, а разбитое стекло — в прочную коробку или пакет с пометкой стекло, чтобы избежать порезов, и так же отправьте в специальный контейнер для стекла или рядом с обычным мусорным контейнером, если другого нет.")  

@bot.message_handler(commands=['paper'])
def send_mem(message):
    img_name = random.choice(os.listdir('images'))  # Случайным образом выбираем изображение
    with open(f'images/{img_name}', 'rb') as f:
        # Отправляем фото, выбранное случайным образом
        bot.send_photo(message.chat.id, f)

bot.polling()
