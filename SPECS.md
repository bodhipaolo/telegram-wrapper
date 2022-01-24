# SPECS

- python telegram bot: https://github.com/python-telegram-bot/python-telegram-bot ```pip install python-telegram-bot```
- botogram:  https://botogram.dev https://github.com/python-botogram/botogram ```pip install botogram2```

## simple commands and callbacks

message with buttons to callback
```
@bot.command("direct", hidden=True)
def direct_command(chat, message, args):
    btns = botogram.Buttons()
    btns[0].callback("Generic", "first", "")
    btns[0].callback("Secondary", "second", "")
    chat.send("some message", attach=btns, syntax="markdown")
```

callback
```
@bot.callback("first")
def first_callback(query, data, chat, message):
    chat.send("some message", syntax="markdown")
```

send photo
```
bot.chat(specuser).send_photo(photofilepath)
```


## send message to different users than the chat

send message to different user than the chat
```
bot.chat(config['admin']).send("some message", syntax="markdown")
```

## timers

timer. do something each number of seconds
```
@bot.timer(600)
def notify(bot):
    # notifications to be sent
```

## message detect

detect a message received from a user by a regular expression. in this example if an email is detected as a message something is done
```
@bot.message_matches(r'^(\w|\.|\_|\-)+[@](\w|\_|\-|\.)+[.]\w{2,3}$')
def email_set(chat, message, matches):
```

preprocessing. message is evaluated before commands being detected
```
@bot.before_processing
def before_processing_message(chat,message):
    # some work on incoming messages is done
```


