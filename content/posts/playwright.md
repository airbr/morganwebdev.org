---
title: "Playwright: My intro"
date: 2022-08-13T12:00:00-08:00
draft: false
tags: 
    - Playwright
    - E2E
    - Testing
    - Browsers
    - Headless
    - Codegen
    - HTML
    - JavaScript
    - Github
    - CI
    - CD
    - Docker
---

I am _enamored_ with [Playwright](https://playwright.dev/). End to end integration testing is a huge topic but I can tell you just a few things about my experience from helping to integrate JavaScript E2E tests at work and in my spare time projects:

![](/playwright-logo.svg)

 First, I have to say I am sure I would have been enamored with experiencing the joy and utility of [E2E](https://www.contentstack.com/blog/tech-talk/what-you-need-to-know-about-e2e-testing-with-playwright/) testing with other frameworks as well including [Cypress](https://www.cypress.io/) or [TestCafe](https://testcafe.io/) but Playwright is my first. 
 
 Getting into E2E is like opening a huge new world, a sub-world within development. There is a lot of competition to be the best framework and everyone wins by this dynamic, there are even brawling battle like events such as [this one from Applitools where Playwright and Cypress face off against each other](https://applitools.com/cypress-vs-playwright-rematch-webinar/). There are lots of blogs and article that say one is better than the other - [like this example from 2021](https://alisterbscott.com/2021/10/27/five-reasons-why-playwright-is-better-than-cypress/)- but this blog is mostly just my enamorment with Playwright as my first library of this kind. 

### Background
I worked at implementing a E2E suite with Playwright for a Fortune 500 company. This was intended as a supplement to the core testing regime and not to replace an experienced QA/QC department. In my role I was primarily a fast follower. I introduced some concepts but it was mostly following behind the masterful work of a coworker who really brought a lot of velocity to the project. 

The focus of the testing was roughly a kind of 80/20 rule. We focused on the 20% of features that were most critical and important to 80%+ of the sites functionality. The goal was to optimize the tests for the "happy path": the path that users were most likely to take when making a purchase such as landing on the homepage, entering a search term, clicking on a product. The tests were intended to be run as [smoke tests](https://en.wikipedia.org/wiki/Smoke_testing_(software)) before deployments and during increasingly test driven development. 

Since gaining this initial experience I have in my spare time added some really basic E2E tests to my personal website that runs everytime I push commits on that repo to GitHub via Github Actions- [Recent Example run](https://github.com/airbr/newpersonal/runs/6840538620?check_suite_focus=true). I have also introduced Playwright testing to a non-profit I volunteer for. It has been great all around. 

### A couple of observations

* Async/Await and [Auto-waiting](https://playwright.dev/docs/actionability) = tests that read like what you are trying to do

Check out this basic example from my website:

```
test('github link works', async ({ page }) => {
  await page.goto('https://morganwebdev.com');
  const github = page.locator("a[href='https://github.com/airbr']");
  await expect(github).toHaveCount(1);
  await github.click();
  const name = page.locator(".vcard-fullname");
  await expect(name).toHaveCount(1);
  await expect(name).toHaveText('Morgan Murrah');
});
```

To me, this test just reads like what I want it to. "Go to my website, locate a github URL, expect it there to be 1 of them, click it, check for my name...". Auto-waiting makes all this feel simple and clean rather than needing to sprinkle in things to check for visibility or even gasp... timeouts. Things get so much more complex than this but this fundamental feature baked into the library makes things so much more approachable.

* [Minimalist feeling installation](https://playwright.dev/docs/intro)
    1.   Do the usual `npx install`...
    2.   Install browsers? if not already installed
    3.   Then run the test. From anywhere. [Docker Container](https://playwright.dev/docs/docker)? Local? On a spare machine? On the cloud somewhere? So many options!


* People get REALLY into configuration. It is possible to run a huge battery of tests across different devices with minimal config too.

    I could just link a bunch of resources but basically, Playwright allows for an incredible amount of configuration. The complexities of E2E testing comes from things like handling multiple auth states and special environmental things. Playwright seems to be handling these well by all indications I can see- I don't read of any burning complaints in this area.

    It is really neat how you can with a [few lines of config set up many mobile and desktop devices](https://github.com/microsoft/playwright/blob/main/packages/playwright-core/src/server/deviceDescriptorsSource.json):

    ![](/tests.png)

* The Community seems vibrant

    The [Slack community for Playwright](https://aka.ms/playwright-slack) gives me hope that it will be a long lived software project. There is a vibrancy to the questions asked and people hopping in saying they have switched to Playwright. There may not be as many Stack Overflow questions as for Cypress... but hey, thats just one metric.

* The Tooling inspires confidence

    Playwright comes out of the box with an [HTML Report feature](https://playwright.dev/docs/test-reporters#html-reporter). Its just one feature that makes the experience feel nice- especially if you expect other people to be interacting with the tests that may not be as directly technical. There are other features such as code generation that helps a lot.

Mainly I am just excited to have made headway into the world of E2E testing and for the moment Playwright has me enamored.

I intend to write further posts on this topic.