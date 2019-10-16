---
layout: post
current: post
cover:  assets/images/posts/post1.jpg
navigation: True
title: A new django admin experience
date: 2019-10-16 10:00:00
tags: [Web Applications, Baton]
class: post-template
subclass: 'post'
author: abidibo
---

What about a cool, modern and responsive django admin template?

Django is a great framework, it let's you build complex web applications quickly and reliably. All the front-end stuff is up to the developer, while the back-end can be auto-generated registering your apps to the django admin application. That's great, because you can focus on how the application will look like, having most of the boring and repetitive backoffice work done.

The django default admin theme has changed over the years, and at the time of this writing it is almost fully responsive. But we think it's too minimal, it lacks a convenient sidebar menu and some teaks to make large forms more readable.

![django-baton index page](/assets/images/posts/django-baton.jpg)

Here comes [django-baton](https://www.github.com/otto-torino/django-baton), a fully responsive django admin theme, based on **Bootstrap 4** and **FontAwesome 5** (free edition). Let's take a look at its main features:

- fully responsive
- custom and flexible sidebar menu (titles, apps, models and free voices supported)
- form tabs out of the box (just set some css classes)
- custom text input filters
- lazy loading and preview of the uploaded images
- index dashboard with google analytics widgets
- easy customizable recompiling the js app

The philosophy behind django-baton is: **overwrite as few django stuff as possible**.    
Such philosophy assures a great compatibility among new django releases.

We developed **django-baton** for us, and for you. It's free to use (**MIT License**), as almost any other project we develop. Try it, and let us know how do you feel about it.

Need help? [Contact us](mailto:mail@otto.to.it).

**We can also create a new brand and custom django-baton version for your project**, add components and functionality, create new widgets or write the entire backend for you if necessary, **we're quite good and fast at doing it.**
