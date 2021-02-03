---
title: Running Cypress Test Script on multiple URLs
excerpt: >-
  Is it possible to test multiple URLs at once with Cypress? Let's find out!
date: 2021-02-03
thumb_img_path: images/time.png
content_img_path: images/mallorca.jpg
layout: post
---

![MultipleURLs](images/time.png)

##### Today we will create Cypress Testing Script that will be performed on multiple URLs. Let's start!

First we need to create **Environment Variables** in _cypress.json_ file. Those variables will store our URLs but also usernames and passwords, needed in login process:

![CypressJson](images/cypressjson.png)

Now, we can create a **Testing Script** that will be perfomed on all URLs that we specified in our _cypress.json_ file. Let's say we want to check if **site version** is correct across all our URLs:

![TestingScript](images/siteversion.png)

Because the **login process** is a step that is repeated frequently during testing, let's say we are testing betting platforms and we want to log in and place a bet on every platform, using it's own minimum stake value. First login:

![Login](images/login.png)

After logging in, in case there are some **additional steps** for specific URL required, like for example accepting **Payment History**, we can use _flags_ that we set up in _cypress.json_ file:

![Flag](images/flag.png)

Now, after we checked that site version is correct and we are logged in, let's place a bet on every platform, using it's own minimum stake value. One of the way of doing that, is to use **clientConfig**:

![BetPlacement](images/betplacement.png)

Hope this article was helpful. The whole script can be found on my github profile:

[GitHub-Repository](https://github.com/JJaworski93/cypressSameTestManyURLs)

Thanks for reading!