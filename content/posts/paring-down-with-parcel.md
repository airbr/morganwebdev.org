---
title: "Paring down with Parcel.js"
date: 2021-06-11T12:00:00-08:00
draft: false
tags: 
    - Parcel.js
    - Personal website
    - Bundler
    - HTML
    - CSS
    - Devices
    - ARIA
    - SVG
    - TinyIcons
---

This is a small blog about how I pared down my personal website to a single page of HTML bundled with parcel.js. This was a change from a PWA Vue-CLI generated site using Webpack. I write this to express my appreciation of making maintenance easy and simplicity where possible.

 [Link to the Repository](https://github.com/airbr/newpersonal)

# What I want out of a personal website or 'my personal bag of hyperlinks'.

I want people to be able to click and find almost my entire web presence linked from one place on mobile or desktop. I want the screen to load everything they need to see without the user needing to access any menus or dropdowns or nav. Some icons (Thank you Super Tiny Icons) made into buttons and some hyperlinks is all I need to give an interested user the tools to navigate my entire web presence/contact information. Additionlly I made use of a CSS library called devices for a design.

There is a popular service called [Linktree](https://linktr.ee/) which I would compare to what I am trying to accomplish with my website in practical terms. I am not looking to provide a comprehensive portfolio experience in one place rather I want to give links for my presence on the web or important links to find out about me.

### A recent screenshot of morganwebdev.com:

![https://www.morganwebdev.com](/screenshot.png)

# The old...

If you [peruse the history](https://github.com/airbr/newpersonal/commit/a7d6519a49ae58178c97ce07a34dca77da805d03) of the repo you will see that my personal website was once a Progressive Web App with limited features. There was simply too much overhead - I never really learned the Vue CLI ecosystem and yet I had it at the core of my personal website. I got good Lighthouse Audit scores but I decided to cut it down and learn some new tools about keeping it simple.

# Enter Parcel.js

[Parcel.js bills itself as the "Blazing fast, zero configuration web application bundler"](https://parceljs.org/). Compared to Webpack it is a breeze and just the right amount of optimization for my simple one page website.

Per the ReadMe:

>In version 4.0 I greatly simplified this repository down and moved the deployment from Firebase to Netlify. I removed dozens of dependencies from the package.json and simplified it down to two parcel.js commands. 

`npm run serve` to run the site.

`npm run build` to generate the site.

As per the description: zero config.


# Conclusion:

Ask yourself what are you really trying to accomplish, it will help you find the right size tool- for the job. In this instance... I am just trying to accomplish a single page of static content. I found joy working with parcel.js for the size of this project.

# Visit [morganwebdev.com](https://morganwebdev.com) today :D





