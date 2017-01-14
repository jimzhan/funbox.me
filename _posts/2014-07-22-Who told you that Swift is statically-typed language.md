---
layout:     post
title:      Who told you that Swift is statically-typed language?
date:       2014-07-22 23:29:10 +0800
tags: [technote, Swift]
---

![Apple Swift](/assets/apple_swift.jpg)

OK, I lied about it. Swift is indeed statically-typed. But if you have ever tried using JSON in it, you’ll know what I mean & where the pain is.

This is a pretty simple functional helper but it took me nearly an hour to finally figure it out what the heck was really going on:

```swift
json["features"].array?.map({ item in (item.string as String) })
```

First you need to ensure *features* from *json* is optional/mandatory(!), then in *map* you’ll still need to explicitly downcast a strong-typed String to a String using *as*.

Oops...did I forget to mention that the *json* object is a *JSONValue*  which has been handled by [SwiftJSON](https://github.com/lingoer/SwiftyJSON) to help you to get rid of tons of ? and ! already?

*Swift* looks so great from the very first sign only, when digging deeper and deeper, it’s a schizophrenic language which is just trying to make itself looks dynamic while its statically-typed from its blood and deep inside its heart, and, it’s incomplete.
