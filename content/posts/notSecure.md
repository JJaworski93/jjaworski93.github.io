---
title: Https but still not secure?
excerpt: >-
  Does your URL start with HTTPS but still is marked as not secure? - Possible solution.
date: 2021-06-03
thumb_img_path: images/notsecuree.png
content_img_path: images/mallorca.jpg
layout: post
---

![NotSecure](images/notsecuree.png)

##### Does your URL start with HTTPS but still is marked as not secure? Let's take a closer look at it.

HTTPS stands for “Hypertext Transfer Protocol Secure”. It allows for the secure flow of information between a server and client. It may happen that although your URL starts with HTTPS and there is nothing wrong with your SSL certificate, web browsers will indicate that connection to your site is not secure:

![NotSecureConnection](images/notsecureee.png)

If this is a case, most likely it is caused by:

* calls to a non-secure 3rd party resources like images

You can investigate it with Chrome using DevTools. To do that, right-click anywhere on the page and choose “Inspect”. Once DevTools is open, navigate to “Security”:

![DevToolsSecurity](images/notsecureeee.png)

Here you will be able to check what is causing your page to be considered as not secure. Also, if you will refresh the page, Chrome DevTools will show you the exact resources that are causing the issues:

![httpResources](images/notsecureeeee.png)

![networkPanel](images/notsecureeeeee.png)

As we can see in the above case, the problem was caused by one of the images that our webpage uses (image URL starts with http:// instead of https://). This is a common case where a website uses images from secondary domains. Unfortunately, if we use resources from secondary domains which are not secure - our page will also be considered as not secure. 

To solve this _"HTTPS but still not secure"_ problem, you could choose a different secure host for your resources. Also, if you own this secondary domain - you can consider migrating it to HTTPS.

Thanks for reading!