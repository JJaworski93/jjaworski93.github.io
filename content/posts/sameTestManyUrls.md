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

First we need to create **Environment Variables** in *cypress.json* file. Those variables will store our URLs but also usernames and passwords, needed in login process:

```JSON
{  
    "ignoreTestFiles": "*/examples/",
    "viewportHeight": 1080,
    "viewportWidth": 1920,
    "pageLoadTimeout": 20000,
    "defaultCommandTimeout": 8000,
    "retries": 3,
    "env": {
        "URL1.be": {
           "url": "https://url1.be",
           "username": "uname",
           "password": "pword"
        },
        "URL1.ch": {
           "url": "https://url1.ch",
           "username": "uname",
           "password": "pword"
        },
        "URL1.com": {
           "url": "https://url1.com",
           "username": "uname",
           "password": "pword",
           "requiresPaymentHistory": true
        }
}
```

Now, we can create a **Testing Script** that will be perfomed on all URLs that we specified in our _cypress.json_ file. Let's say we want to check if **site version** is correct across all our URLs:

```Javascript
describe('Same Test multiple URLs', () => {

    const expectedSiteVersion = '987654321';

    const envConfig = Cypress.env();
    const envKeys = Object.keys(envConfig);

    for (const key of envKeys) {
    const env = envConfig[key];

    // to perform test only on url1.com you can use:
    // const key = '';
    // const env = envConfig['URL1.com'];


    it(`test site version for: ${key}`, () => {
        cy.request(`${env.url}/site/version`)
          .its('body').should('include', expectedSiteVersion);
    })
  }
})
```

Because the **login process** is a step that is repeated frequently during testing, let's say we are testing betting platforms and we want to log in and place a bet on every platform, using it's own minimum stake value. First login:

```JavaScript
it(`login & bet placement test: ${key}`, () => {

   // first we check login function for all URLs
   cy.visit(`${env.url}`);
   cy.get('[href*="labelhost/login"]').should("exist");
   cy.get('[href*="labelhost/login"]').click();
   cy.get('lh-login').should("exist");
   cy.get('#username').type(`${env.username}`);
   cy.get('#password').type(`${env.password}`);
   cy.get('.login').click();

   // check if login window is closed after successful login
   cy.get('lh-login-dialog').should("not.exist");
```

After logging in, in case there are some **additional steps** for specific URL required, like for example accepting **Payment History**, we can use _flags_ that we set up in _cypress.json_ file:

```JavaScript
if (env.requiresPaymentHistory) {
    cy.get('#monthly-payment-hist').find('.btn').should("exist");
    cy.get('#monthly-payment-hist').find('.btn').click();
}
```

Now, after we checked that site version is correct and we are logged in, let's place a bet on every platform, using it's own minimum stake value. One of the way of doing that, is to use **clientConfig**:

```js
cy.window()
  .its('clientConfig')
  .then((cfg) => {
      const minStake = cfg.msSportsUser.configSettings.minimumStake;
      console.log(minStake);
      cy.get('.grid-option').should("exist");
      cy.get('.grid-option').eq(0).click();
      cy.get('.stake-input-value').should("exist");
      cy.get('.stake-input-value').type(minStake);
      cy.get('#betplacement-btn').click();
      cy.get('#betplacement-msg').contains('Bet placed');
     })
   })
  }
})
```

Hope this article was helpful. The whole script can be found on my github profile:

[GitHub-Repository](https://github.com/JJaworski93/cypressSameTestManyURLs)

Thanks for reading!