---
title: Cypress - software testing tool - advantages and disadvantages
excerpt: >-
  There is no need to explain to anyone how important software testing is. Let's check the pros and cons of using Cypress.
date: 2021-03-04
thumb_img_path: images/cypress.png
content_img_path: images/mallorca.jpg
layout: post
---

![Cypress](images/cypress.png)

##### To convince anyone how beneficial automated software testing is, is not needed.

**Automated software testing** is much faster than manual testing and what is most important - it is repeatable. We need to remember however, that automated testing should be a great supplement and support for manual testing - not a replacement. The test script works only as it was programmed and does a great job. However, nothing can replace the skilled eye of an experienced tester.

Cypress is a **JavaScript-based end-to-end framework** dedicated for testing. Besides end-to-end testing, cypress turns to be very handy when it comes to **unit and integration testing**. It doesn't use **Selenium**, but it can be configured to use **Cucumber** if needed. It runs in the browser simplifying asynchronous testing. Cypress is built on top of **Mocha** and makes testing easier and more pleasant, in line with the principle:

>Test your code, not your patience.

Cypress is **open-source** and offers an useful **dashboard**. Test runner, among others, allows you to view your tests' progress/result and preview logs. 

This great tool can be installed with just one command line:

_npm install cypress_

Let's move on to the **pros and cons** you need to know. **Benefits of using Cypress**: 

* Test runner and cypress dashboard captures precisely what happens at the time of test execution, giving you a complete picture of what is currently happening with the application and how it behaves. You are able to see what happens before and after some action in a specific command. It gives you also possibility to interact with the test and provide some changes if you wish so.
* A built-in mechanism that handles waiting for DOM elements, makes commands like sleep or wait unnecessary. Maximum waiting time as default is set to 10.000ms but you can modify it.
* With a *--parallel flag* you can run recorded tests in parallel across multiple virtual machines.
* Cypress supports browsers such as Chrome, Firefox and Edge. It has also a built-in Electron (lightweight) browser. 
* It provides a great debugging tool, so you can easily check why your tests are failing. 
* It documents the entire testing process in great detail and allows you to execute commands in real-time with live preview.
* Cypress supports interacting with an API and has a built-in API Testing Library that is really easy to use. 

**Disadvantages of using Cypress**:

* Cypress doesn't support IE, Safari nor Opera browser. Also, there is no support for multiple tabs. Besides, there is a limited support for iFrames.
* It doesn't support any other, than JS, programming languages.
* Cypress doesn't support mobile testing. However, you can test some functionality of mobile web browsers or test mobile applications (that are developed in a browser) with [Ionic framework](https://ionicframework.com/). In case you would like to know more, here is useful article about [Ionic & Cypress](https://www.cypress.io/blog/2020/07/08/end-to-end-testing-mobile-apps-with-ionic-and-cypress/).

Thanks for reading!