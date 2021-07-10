---
title: You can now customize the subreddits used in the meme API
date: 2021/7/9
description: This post will show you how.
tag: announcement
author: AR
---

# You can now customize the subreddits used in the meme API
Our super epic meme endpoint gets even more epic! You can now add custom subreddits to the list of subreddits or use only your own specified list of subreddits to get memes from.

## Add to the subreddit list
You can add to the subreddit list by using the `?addthese` query. The value must be the subreddits split with `,` if there are multiple. This will add your subreddits to the default list of subreddits for that request.

## Use and only use your own subreddit list 
You can use your own subreddit list without using the default subreddits by using the `?useonly` query. Like addthese, you have to split the subreddits with `,` if you are adding multiple. This will remove the default subreddits and add your subreddits for that request. This can be used if for example you only want me_irl and woooosh memes.

## More updates
All updates are usually sent in the updates channel of our [Discord](https://discord.gg/new), and are sometimes posted on this blog. You should join the Discord if you want to see all the updates and not just major ones.

