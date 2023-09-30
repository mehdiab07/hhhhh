import discord
from discord.ext import commands
import asyncio
import execjs

# Create a bot instance with a prefix
bot = commands.Bot(command_prefix='!')

# Event handler for when the bot is ready
@bot.event
async def on_ready():
    print(f'Logged in as {bot.user.name}')

# Define a command for code execution
@bot.command()
async def execute(ctx, *, code):
    try:
        # Create a JavaScript context for code execution
        ctx_js = execjs.compile('')
        
        # Execute the provided code and get the result
        with ctx_js:
            result = ctx_js.eval(code)
        
        # Send the result as a message
        await ctx.send(f"Result:\n```\n{result}```")
    
    except Exception as e:
        await ctx.send(f"An error occurred:\n```\n{e}```")

# Run the bot with your token
bot.run('YOUR_TOKEN_HERE')
