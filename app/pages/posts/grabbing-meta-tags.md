---
title: Grabbing metadata information from a website
date: 2021/7/9
description: This post will show you how to grab metadata information from any website as JSON.
tag: cheerio
author: AR & RemiixInc
---

# Grabbing metadata information from a website
Metadata information is used on almost all social media websites as a way to get basic information like a title, an image, site name, and description from the website sent. But how do you implement this into your own projects? This short post will show you how to.

## Method 1 (Easiest): Use a meta grabber API
This method is pretty simple. All you have to do is send a request to an API and get the meta data information of the website as JSON.
Here's how to do this using TotallyUsefulAPI's meta grabber:
```js
import { get } from 'axios';
// Import the Axios module (or node-fetch, depends on you)
get('https://totallyusefulapi.ml/api/meta?url=https://www.google.com').then(res => {
    // Send the request and set the response as the res variable
    const metadata = res.data
    // Set the data of the response as the metadata variable
    console.log(metadata)
    // Log the response data to the console (or do whatever you want to do with it)
    // {"title":"Google","description":"Search the world's information, including webpages, images, videos and more. Google has many special features to help you find exactly what you're looking for."}
}).catch(e => {
    console.log('An error occured')
})
```

## Method 2: Use Cheerio
RemiixInc explains this pretty well on [this](https://dev.to/remiix/getting-website-meta-tags-with-node-js-1li5) post on his blog, but I'll explain it simply.
You can a JavaScript module named "Cheerio" which turns HTML elements into JSON, and you can find the meta tags using it.
Here's an example:
```js
import { load } from 'cheerio';
// Import cheerio
import { get } from 'axios';
// Import Axios
get('https://www.google.com').then(res => {
    // Send the request to the website you wish to get the meta tags for, and set the res variable as the response
    const data = res.data
    // Set the data variable as the website's HTML
    var title = $('meta[property="og:title"]').attr('content') || $('title').text() || $('meta[name="title"]').attr('content')
    var description = $('meta[property="og:description"]').attr('content') || $('meta[name="description"]').attr('content')
    var url = $('meta[property="og:url"]').attr('content')
    var site_name = $('meta[property="og:site_name"]').attr('content')
    var image = $('meta[property="og:image"]').attr('content') || $('meta[property="og:image:url"]').attr('content')
    var icon = $('link[rel="icon"]').attr('href') || $('link[rel="shortcut icon"]').attr('href')
    var keywords = $('meta[property="og:keywords"]').attr('content') || $('meta[name="keywords"]').attr('content')
    // Load the website's meta data
    const metatags = {
        "title": title || null,
        "description" description || null,
        "url" url || null,
        "site_name": site_name || null,
        "image": image || null,
        "icon": icon || null,
        "keywords" keywords || null
    }
    // Turn all meta tags into one object
})
```

## And that's it
If you used any of the methods above, you should now have the meta tags for any website as a JSON object.
If you like what you see, feel free to join our [Discord](https://discord.gg/new), and check out our [API](https://totallyusefulapi.ml) for more cool tools.