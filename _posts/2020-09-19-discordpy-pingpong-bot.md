---
layout: post
title: "디스코드 인공지능 봇 만들기"
tags: [python, discord.py, bot]
comments: true
---

discord.py 모듈로 핑퐁 빌더를 이용해서 나만의 인공지능 봇을 만들어봅시다!

---

이 글에서는 제가 만든 [PingPongTool](https://pypi.org/project/PingPongTool/) 모듈을 사용하여 설명합니다.

## 모듈 설치

```
pip install discord
pip install PingPongTool
```

## 전체 코드

```py
import discord
from discord.ext import commands
from PingPongTool import PingPong
from random import randint

def RandomColor():
    return randint(0, 0xFFFFFF)

TOKEN = "이곳에 봇 토큰을 넣으세요"
Authorization = "이곳에 인증 토큰을 넣으세요"
URL = "이곳에 커스텀 API 링크를 넣으세요"

bot = commands.Bot(command_prefix=['!', '핑퐁아 '])
Ping = PingPong(URL, Authorization)


@bot.listen()
async def on_command_error(ctx, error):
    if type(error) is commands.errors.CommandNotFound:
        data = await Ping.Pong(ctx.author.id, ctx.message.content, NoTopic=False)
        embed = discord.Embed(
            title="핑퐁",
            description=data['text'],
            color=RandomColor()
        )
        embed.set_footer(text="Using PingPongTool")
        if data['image']:
            embed.set_image(url=data['image'])
        await ctx.send(embed=embed)


@bot.command(name="따라해")
async def Echo(ctx, *, text: str):
    await ctx.send(text)

bot.run(TOKEN)
```

## 코드 설명

1. 필요한 모듈들을 불러옵니다.
```py
import discord
from discord.ext import commands
from PingPongTool import PingPong
from random import randint
```

2. 임베드에 쓰일 랜덤 색깔 함수를 선언합니다.
```py
def RandomColor():
    return randint(0, 0xFFFFFF)
```

3. 정보들이 담긴 변수들을 선언합니다
```py
TOKEN = "이곳에 봇 토큰을 넣으세요"
Authorization = "이곳에 인증 토큰을 넣으세요"
URL = "이곳에 커스텀 API 링크를 넣으세요"
```

4. 디스코드 봇 클래스와 핑퐁 클래스를 선언합니다.
```py
bot = commands.Bot(command_prefix=['!', '핑퐁아 '])  # 커맨드 프리픽스는 !, 핑퐁아
Ping = PingPong(URL, Authorization)
```

5. 커맨드가 없으면 핑퐁 빌더를 호출합니다.
```py
@bot.listen()
async def on_command_error(ctx, error):
    if type(error) is commands.errors.CommandNotFound:
        data = await Ping.Pong(ctx.author.id, ctx.message.content, NoTopic=False)
        embed = discord.Embed(
            title="핑퐁",
            description=data['text'],
            color=RandomColor()
        )
        embed.set_footer(text="Using PingPongTool")
        if data['image']:
            embed.set_image(url=data['image'])
        await ctx.send(embed=embed)
```
---
### 5번 상세 설명
5-1. 커맨드가 존재하지 않는 경우에만 실행되도록 합니다.
```py
@bot.listen()
async def on_command_error(ctx, error):
    if type(error) is commands.errors.CommandNotFound:
```

5-2. 핑퐁 빌더를 호출합니다.
```py
data = await Ping.Pong(ctx.author.id, ctx.message.content, NoTopic=False)
```

5-3. 임베드를 생성합니다.
```py
        embed = discord.Embed(
            title="핑퐁",  # 임베드 타이틀
            description=data['text'],  # 임베드 설명
            color=RandomColor()  # 임베드 색깔
        )
        embed.set_footer(text="Using PingPongTool")  # 임베드 푸터
```

5-4. 만약 핑퐁 빌더에서 이미지가 같이 온 경우 임베드에 이미지를 삽입합니다.
```py
        if data['image']:
            embed.set_image(url=data['image'])
```

5-5. 커맨드를 실행한 채널에 메시지를 전송합니다.
```py
        await ctx.send(embed=embed)
```
---

6. 핑퐁 빌더가 아닌 일반 커맨드를 만듭니다.
```py
@bot.command(name="따라해")  # 커맨드 이름
async def Echo(ctx, *, text: str):  # 커맨드 다음으로 모든 문자열을 text 변수에 넣기
    await ctx.send(text)  # 메시지 전송
```

## 마무리
여기까지 잘 따라오셨죠?

궁금한게 있으시다면 댓글 또는 디스코드 (Minibox#3332)로 편하게 물어봐주세요!