import discord
from discord.ext import commands
import configparser

intents = discord.Intents.default()
intents.members = True

bot = commands.Bot(command_prefix='!', intents=intents)

# Function to read configuration settings from a file
def read_config():
    config = configparser.ConfigParser()
    config.read('config.ini')
    return config['WelcomeBot']

@bot.event
async def on_ready():
    print(f'Logged in as {bot.user.name}')
    print('------')

@bot.event
async def on_member_join(member):
    config = read_config()
    welcome_channel_id = int(config.get('welcome_channel_id', ''))
    welcome_message = config.get('welcome_message', 'Welcome to the server, {member.mention}!')

    if welcome_channel_id:
        welcome_channel = member.guild.get_channel(welcome_channel_id)
        if welcome_channel:
            await welcome_channel.send(welcome_message.format(member=member))

bot.run('YOUR_BOT_TOKEN')

