---
title: How to make a meme Discord bot using the Discord API and TUA
date: 2021/7/10
description: This post will show you how to make a Discord bot that automatically sends memes to a Discord channel.
tag: discord
author: AR
---

# How to automatically send memes to a Discord channel using the Discord API and TUA
Discord is an amazing chat app for everyday usage, and it has lots of bots, some of which allow you to make meme feeds in a Discord channel, but most of them are paid, and cannot be used unless you buy a subscription. This post will show you how to use TotallyUsefulAPI to grab a meme and the Discord API to send it to a Discord channel on a set interval.

## 1. Generate a Discord token and invite the bot to your server
Firstly, go to the [Discord Developer Portal](https://discord.com/developers/applications), and click on the "New Application" button
![](https://imgur.com/QWS4LGP.png)

Nextly, put in a name for your bot, and hit the create button
![](https://imgur.com/RROxUeQ.png)

Now click on the bot tab on the left panel
![](https://imgur.com/ryQQgdy.png)

And now click the Add Bot button, and click "Yes, do it!" on the modal that appears
![](https://imgur.com/MhCXd5y.png)

Now, click on the OAuth2 button on the left panel
![](https://imgur.com/fsydLCE.png)

Scroll down until you see "OAuth2 URL Generator", and select the buttons shown in the image below
![](https://imgur.com/UFu7AHg.png)

Now copy the link, and open it in a new tab
![](https://imgur.com/YVrOXBh.png)

Select the server to add the bot to
![](https://imgur.com/g3JGQ5b.png)

Click on continue
![](https://imgur.com/ugqGAO4.png)

Authorize the bot and fill in the Captcha
![](https://imgur.com/kgzmyOz.png)

## 2. Making the bot
- Go to the bot tab in the developer portal, and copy your bot's token
![](https://imgur.com/rl828yJ.png)

- Create a new folder, and create a file named "index.js" in it
- Open your terminal, cd to the bots directory and type `npm i discord.js axios`. Now keep your terminal open.
- Paste the following code in the index.js file, and replace YOUR BOTS TOKEN and CHANNEL ID with the values it's asking for. To get a channel id, go to settings > advanced > developer mode.
```
const Discord = require('discord.js')
const client = new Discord.Client()
const { get } = require('axios')
const channel = "CHANNEL ID"
const token = "YOUR BOTS TOKEN"

client.on('ready', () => {
    console.log('Ready!')
})

setInterval(() => {
    get('https://totallyusefulapi.ml/api/random/meme').then(res => {
       client.channels.cache.get(channel).send(new Discord.MessageEmbed().setTitle(res.data.title || "No title", res.data.postlink).setImage(res.data.fullmedia).setAuthor(res.data.subreddit + " | u/" + res.data.author).setFooter(`Upvotes: ${res.data.upvotes} | Downvotes: ${res.data.downvotes}`).setDescription(`Created at <t:${res.data.createdat}>`).setColor("GREEN"))
    })
}, 600000)

client.login(token)
```

And now run `node .` in your terminal!

## Thanks for reading!
Join our discord at discord.gg/new