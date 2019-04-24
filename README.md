# [WIP] telegrep
Monitor journald in real time and get Telegram messages when patterns match.

## Usage
Copy `settings.config.TEMPLATE` to `settings.config` and enter both your bot's
token, as well as the chat id of the conversation you have with it.

If you don't have a Telegram bot, go ahead and
[create one](https://core.telegram.org/bots).
This will give you the access token for your bot.
Next, you need to start a conversation with it and send at least one message.
Then you can do `curl https://api.telegram.org/bot<TOKEN>/getUpdates` and
the JSON response will contain an `id` value in the `chat` object.
This is your chat id.

Once everything is configured, simply run `./telegrep` and whenever the
pattern you defined in the configuration is encountered in the systemd journal,
you will receive a message with that line from the log.

## License
[GNU General Public License v3.0](LICENSE)
