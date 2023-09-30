import discord
from discord.ext import commands

# Create a bot instance with a prefix
bot = commands.Bot(command_prefix='!')

# Event handler for when the bot is ready
@bot.event
async def on_ready():
    print(f'Logged in as {bot.user.name}')

# Event handler for when a new member joins
@bot.event
async def on_member_join(member):
    # Define the welcome message
    welcome_message = f"Welcome to the server, {member.mention}!"
    
    # Send the welcome message to a specific channel (replace 'welcome-channel' with your channel name)
    welcome_channel = discord.utils.get(member.guild.channels, name='welcome-channel')
    if welcome_channel:
        await welcome_channel.send(welcome_message)

# Run the bot with your token
bot.run('YOUR_TOKEN_HERE')

