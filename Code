import discord
from discord.ext import commands
import json
import os

if os.path.exists(os.getcwd() + "/config.json"):

    with open("./config.json") as f:
        configData = json.load(f)

else:
    configTemplate = {"Token": "", "Prefix": "!"}

    with open(os.getcwd() + "/config.json", "w+") as f:
        json.dump(configTemplate, f)

token = configData["Token"]
prefix = configData['Prefix']

bot = commands.Bot(command_prefix='!', intents=discord.Intents.all())

@bot.command()
async def clear(ctx, amount=11):
    await ctx.channel.purge(limit=amount)

@bot.command()
@commands.has_permissions(ban_members=True)
async def ban(ctx, member: discord.Member, *, reason=None):
    await member.ban(reason=reason)
    await ctx.send(f"{member} пошел вон !")

@bot.command()
@commands.has_permissions(kick_members=True)
async def kick(ctx, member: discord.Member, *, reason=None):
    await member.kick(reason=reason)
    await ctx.send(f"{member}  кыш !")

@bot.command()
async def ping(ctx):
    latency = round(bot.latency * 1000, 1)
    await ctx.send(f"Pong! {latency}ms")

@bot.command()
async def hi(ctx, member):
    await ctx.send(f"Hi! {member}")

@bot.command()
async def unban(ctx, member):
    pass


@bot.event
async def on_ready():
    print('Tit is ready!')







bot.run('Bot token')
