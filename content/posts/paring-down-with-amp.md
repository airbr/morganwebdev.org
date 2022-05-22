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

This is a post about my experience of simplifying my personal website down to an AMP page. My philosophy was incremental improvement using the [validator](https://validator.ampproject.org/) and [lighthouse](https://developers.google.com/web/tools/lighthouse) test audits. Additionally I added basic service worker functionality with the `amp-install-serviceworker` tag.

The result is an excellent lighthouse score and a pretty excellent WebPageTest score on Core Web Vitals:

![](https://github.com/airbr/newpersonal/raw/master/readme-assets/lighthouse-2022.png)

![](/static/CWV.png)

I followed a number of steps to achieve this namely size bounding and inlining CSS and using the excellent  [Super Tiny Icons Repository](https://github.com/edent/SuperTinyIcons)

