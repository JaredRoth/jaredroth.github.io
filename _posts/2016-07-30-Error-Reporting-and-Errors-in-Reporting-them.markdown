---
title:  "Error Reporting and Errors in Reporting them"
date: 2016-07-30
---

### Shouldn't be hard

One of the existing issues on the Looking-For project I [mentioned previously]({% post_url 2016-07-20-Joining-an-existing-project %}) was to set up some kind of error tracking system. When I saw that, I immediately thought "I can do this" as well as "that looks hard." So, naturally, I grabbed the issue and started researching and coding like a madman... who's very tired... so not _that_ much.

There are many ways to go about something like this, but since the app is very simple I wanted a similarly simple solution. Luckily someone had already done some research into options os I didn't have to look far. [This handy little gem](http://smartinez87.github.io/exception_notification/) does all the heavy lifting for you _and_ allows you to send your errors pretty much nay way you like. Email? Sent. Campfire? Smoky. Generic Webhook? Um... yes. Slack? Loose or whatever.

In fact, since simple was the name of the game here and this is a Turing project and we all use slack at Turing, I thought that was just swell and ran with it.

### Why so haaard?

After pouring over the documentation and configuring everything as I thought it should be... and setting up the webhook in slack... and creating the appropriate channel (and selecting the appropriate emoji for the bot to use). I was stumped. I couldn't figure out how to actually _use_ this supposedly marvelous gem. I couldn't get an error to log. I tried what I thought was everything to get slack to spit anything out. (Spoiler: it was not everything).

So I continued to read documentation. And blogs. And learn about webhooks from the ground up. And sacrificed a goat or something. And then I gave up for the night. It had been pretty much one entire day of troubleshooting this problem.

### And yet, _so_ easy

The next day I met with an instructor who found the "problem" in, like, 3 minutes. And I felt stupid.

As it turns out. Everything was _already_ set up perfectly (hooray me), I just didn't know how to create an error because I am a doofus. I had continually attempted to trigger 404's... but most of the time we don't want to log those and the gem-creator knew this, so 404's don't get logged... And I didn't realize how incredibly easy it is to create a 500. So, so easy. And that was it. All of a sudden, boom, errors in slack. Yay errors!

Short explanation: The way errors are handled in Rails is pretty nifty but the way this gem intercepts that is even niftier. You don't actually have to _use_ the gem **anywhere**. At all. You literally put two gems in your gemfile and add 4 lines to a config file (one of which is just '}'). That's it.
