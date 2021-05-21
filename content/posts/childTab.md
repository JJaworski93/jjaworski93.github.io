---
title: Is multi-tab testing supported by Cypress?
excerpt: >-
  One of the disadvantages of using Cypress is that it does not support multi-tab.. or does it?
date: 2021-04-01
thumb_img_path: images/screen6.png
content_img_path: images/mallorca.jpg
layout: post
---

![MultiTabs](images/screen6.png)

##### In the previous post I mentioned that Cypress does not support multi-tab testing. But is there anything we can do in some cases? Let's find out.

Let's say that we need to perform an end to end test of our blog. We want to be sure that **included github link** is working properly. First we need to visit our blog:

_cy.visit('ht<span>tps://</span>thebugger.io/');_

Then, in order to check if github link is working, we need to click it and see if the outcome of this action is correct. We can do it with:

_cy.get("a[href*='github.com']").click();_

Locator _a[href*='...']_ is a CSS selector. If you are interested, more about CSS selectors you can find [here](https://www.w3schools.com/cssref/css_selectors.asp). At this point we run into a problem. Our link will open in a **new tab (child tab)** but we won't be able to perfom any further checks on that external link. A solution here might be **removing _target="blank"_** attribute from our link. This will prevent opening a new tab. To achieve that we can modify the above step and instead use:

_cy.get("a[href*='github']").invoke('removeAttr', 'target').click();_

However, this will lead to an error: _"Cypress detected a cross origin error happened on page load"_ and our test will fail, because Cypress runner will notice that our origin link - _thebugger.io_ - is different than our external link - _github.com_. On that stage, if we use Chromium-based browsers, we can do one more thing. We can add **_"chromeWebSecurity": false_** to our cypress.json file:

_"chromeWebSecurity": false_

This will **solve** our issue and even more - it will allow us to continue testing on this child tab. We can log in to the github profile, we can navigate to the specific repository or for example, as a first test, we can check if the correct github profile was opened:

cy.get('.p-nickname').contains('JJaworski93');

Hope you found this article helpful.

Thanks for reading!