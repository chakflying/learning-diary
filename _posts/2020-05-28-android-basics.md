---
layout: post
title: Android Basics
---

Working through the [Google codelabs tutorials](https://codelabs.developers.google.com/codelabs/advanced-android-kotlin-training-notifications/index.html), I am learning the basics about Android. It's interesting to see how tightly coupled the app development process is with the underlying operating system, something that desktop development would never experience. I feel like I still don't know enough about the strange syntaxes of Kotlin. Seems like a lot of method calls are used contextually, like `cancelAll()` just works because it's inside a `NotificationManager`. This is surely easy to use, but it might be difficult to tell where the method definition comes from at a glance.

### Intent

Intent is basically an entry point to your app, that captures the Application Context, and a specific Activity that this intent will launch. A `PendingIntent` will allow other applications or the OS to trigger your app, even if your app is not running. A `Broadcast` is a special Intent that mirror the `pub-sub` design pattern, and you can have `BroadcastReceiver` that process the incoming Intent.

### Fragment

Fragment is basically a view, and the things that need to be started when running the view, such as creating a Notification Channel to send notifications, initialize a `ViewModel` to store UI data and such.

### ViewModel

ViewModel serves to separate data from the UI. Since the UI might get redrawn because of screen-rotation, split-screen and such, we don't want to lose the user entered data when that happens. `ViewModel` helps store that data.

### Strings

No strings that show up in the UI should be in the code. The standard android pattern stores all the strings in a separate file, and retrieve them in code by `applicationContext.getString(R.string.something)`. This allows easy translation and changes to wording, since they are all centralized.
