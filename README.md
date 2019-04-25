# [WIP] telegrep
Monitor journald in real time and get Telegram messages when patterns match.

## Usage
### Getting a Telegram bot
If you don't have a Telegram bot, go ahead and
[create one](https://core.telegram.org/bots).
This will give you the access token for your bot.
Next, you need to start a conversation with it and send at least one message.
Then you can do `curl https://api.telegram.org/bot<TOKEN>/getUpdates` and
the JSON response will contain an `id` value in the `chat` object.
This is your chat id.

### Configuration
Copy `settings.config.TEMPLATE` to `settings.config` and enter both your bot's
token, as well as the chat id of the conversation you have with it.
Then enter your regular expression that you want to watch the journal for.

Once everything is configured, simply run `./telegrep` and whenever the
pattern you defined in the configuration is encountered in the systemd journal,
you will receive a message with that line from the log.

### Installation
Edit `telegrep.service` and change the user to the one you want to run it with.
Also update both paths to point to where you keep the directory.
After that, the installation could be something like this:
```
# Link the unit file to the appropriate location
sudo ln -s /opt/telegrep/telegrep.service /etc/systemd/system/
# Start it
sudo systemctl start telegrep
# Check the status
systemctl status telegrep
# Enable it to start on boot
sudo systemctl enable telegrep
```

## License
[GNU General Public License v3.0](LICENSE)
