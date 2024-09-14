import config
import telebot
import random

bot = telebot.TeleBot(config.token)


# Handle '/start' and '/help'
@bot.message_handler(commands=['help', 'start'])
def send_welcome(message):
    bot.reply_to(message, """\
Hi there, I am EchoBot.
I am here to echo your kind words back to you. Just say anything nice and I'll say the exact same thing to you!\
""")

@bot.message_handler(commands=['generator'])
def passwordgen(message): 
    
    msg = message.text.split(" ") 
    symbols = "+-/*!&$#?=@abcdefghijklnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890"
    length = msg[1]
    password = ''

    for _ in range(int(length)):
        randomised = random.choice(symbols)
        password += randomised
    if msg[2] == 'lower':
        bot.reply_to(message, password.lower())
    elif msg[2] == 'upper':
        bot.reply_to(message, password.upper())
    elif msg[2] == 'nosymbols':
        symb = "+-/*!&$#?=@"
        password = password.translate(str.maketrans('', '', symb))
        bot.reply_to(message, password)
# Handle all other messages with content_type 'text' (content_types defaults to ['text'])
@bot.message_handler(func=lambda message: True)
def echo_message(message):
    bot.reply_to(message, message.text)


bot.infinity_polling()
