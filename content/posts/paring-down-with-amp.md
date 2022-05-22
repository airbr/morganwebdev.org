---
title: "Paring down with AMP"
date: 2022-05-21T12:00:00-08:00
draft: false
tags: 
    - AMP
    - AMPHTML
    - Personal website
    - HTML
    - CSS
    - SVG
    - TinyIcons
    - AMP Validator
    - Lighthouse
    - WebPageTest
---
[![Netlify Status](https://api.netlify.com/api/v1/badges/ed41d932-636f-4c3a-849a-adaaf6498e71/deploy-status)](https://app.netlify.com/sites/sharp-kilby-16c20a/deploys)
# [morganwebdev.com](https://morganwebdev.com)

This is a post about my experience of simplifying my [personal website](https://morganwebdev.com) down to an AMP page. My philosophy was incremental improvement using the [validator](https://validator.ampproject.org/) and [lighthouse](https://developers.google.com/web/tools/lighthouse) test audits as guides. Additionally I added basic service worker functionality with the `amp-install-serviceworker` tag.

The result is an excellent lighthouse score and a pretty excellent WebPageTest score on Core Web Vitals:

![](https://github.com/airbr/newpersonal/raw/master/readme-assets/lighthouse-2022.png)

![](/CWV.png)

I followed a number of steps to achieve this namely size bounding and inlining CSS and using the excellent  [Super Tiny Icons Repository](https://github.com/edent/SuperTinyIcons)


## Goals & Evolution

Like with earlier versions of this site, I wanted someone to be able to find a snapshot of information and links about me that was mobile-first and loaded almost immediately. This led me to think about emulating a device with app-like buttons and I used an earlier version of [devices.css](https://picturepan2.github.io/devices.css/) where I cut the CSS down to the specific device needed for this page.

## Future?

I am considering the future of the website, now that I have achieved a baseline excellent level of performance I could go about adding advanced features.

