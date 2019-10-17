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

Django is a great framework, it lets you build complex web applications quickly and reliably. All the front-end stuff is up to the developer, while the back-end can be auto-generated registering your apps to the django admin application. That's great, because you can focus on how the application will look like, having most of the boring and repetitive backoffice work done.

The django default admin theme has changed over the years, and at the time of this writing it is almost fully responsive. But we think it's too minimal, it lacks a convenient sidebar menu and some tweaks to make large forms more readable.

![django-baton index page](/assets/images/posts/django-baton.jpg)

Here comes [django-baton](https://www.github.com/otto-torino/django-baton), a fully responsive django admin theme, based on **Bootstrap 4** and **FontAwesome 5** (free edition). Let's take a look at its main features.

## Fully responsive

You mainly manage your app contents using a laptop with a full hd screen, but it happens to correct some typos, or fix something wrong your customer did while you're enjoying a beer before dinner. **Baton looks great also at mobile resolutions, and it'll be easy to use with portable devices.**
<p style="display: flex; flex-direction: row; justify-content: center; align-items: center;flex-wrap: wrap;">
  <img src="/assets/images/posts/django-baton-home-mobile.png" alt="home page" />
  <img src="/assets/images/posts/django-baton-menu-mobile.png" alt="menu page" />
</p>

## Custom and flexible sidebar menu

Baton brings to you a nice sidebar menu always visible that lets you surf between different admin section in one click.
It supports different kinds of voices: titles, apps, models and free.

**You can organize menu voices under titles to highlight interconnected modules. You can use models voices to avoid the repetition when an app only has one model, you can define free voices where you set the destination url.**

Flexible, and customizable!

## Form tabs out of the box

How do you feel when your model form becomes huge, with many fields and too many inlines? What if your customer wants to move a "normal" field between inlines? I felt bad... until I wrote Baton, of course.

Baton lets you define form tabs with ease, just adding some css classes to the fieldsets you already define in the django model admin class. A tab can contain only "normal" fields, inlines or both. **Baton tabs are really powerful and the result is an elegant and readable form.**

![django-baton index page](/assets/images/posts/django-baton-tabs.png)


## Custom text input filters

Baton provides a filter class you can use to create text filters. This is a must have when you need to search in many text fields with a certain precision (and so the `search_fields` functionality can't do the job).

``` python
from baton.admin import InputFilter

class CityFilter(InputFilter):
    parameter_name = 'city'
    title = 'City'

    def queryset(self, request, queryset):
        if self.value() is not None:
            search_term = self.value()
            return queryset.filter(
                city__icontains=search_term
            )


@admin.register(Member)
class MemberAdmin(admin.ModelAdmin):
    list_display = ('id', 'lastname', 'firstname', 'email', 'city', )
    list_filter = (CityFilter, )
```

## Lazy loading and preview of uploaded images

The django admin application doesn't offer an image preview of the uploaded files. You can see them opening the given link in a new tab, but often the customers ask for a preview feature, an inline preview of the uploaded file. **Baton will (optionally) show all the uploaded images inline, lazy loading them in order to avoid blocking the page rendering.**

![django-baton index page](/assets/images/posts/django-baton-img-preview.png)

## Index dashboard with google analytics widgets

Let's admit it: the default admin index page it's quite... unsightly.
In many cases you can override the index template displaying some sort of statistics in order to mimic a dashboard. Sometimes you simply don't have meaningful statistics to show, or any other content to add, but you have google analytics collecting stats for you!

**With Baton is super easy to get an analytics dashboard displaying many widgets** (powered with google charts) which give you a brief idea of how your visits are going on. Baton speaks with the google analytics API to do so, and you just need the create the necessary credentials.

![django-baton index page](/assets/images/posts/django-baton-analytics.png)

## Easy customizable recompiling the js app

We gave Baton a nice looking suit, but there are cases in which you customer asks for more customization also in the admin area: colors, backgrounds, fonts and so on...

With Baton you can do it without overriding any template. Baton is mostly a compiled js app which brings together all its styles. The js app is compiled using webpack and included in the `base_site` template. You can just take the app source, change some **sass** variables, recompile it and serve the same static file from an app declared in the `INSTALLED_APPS` before baton. Easy!

## And now?

The philosophy behind django-baton is: **overwrite as few django stuff as possible**.    
Such philosophy assures a great compatibility among new django releases.

We developed **django-baton** for us, and for you. It's free to use (**MIT License**), as almost any other project we develop. Try it, and let us know how do you feel about it.

Need help? [Contact us](mailto:mail@otto.to.it).

**We can also create a new brand and custom django-baton version for your project**, add components and functionality, create new widgets or write the entire backend for you if necessary, **we're quite good and fast in doing it.**
