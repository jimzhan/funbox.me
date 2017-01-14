---
layout: post
title:  Pitfall of Using AFNetworking in Swift
date:   2014-07-17 22:34:52 +0800
tags: [Swift, Objective-C]
---

Having gone through a whole boring day for figuring out what the hell was wrong with my JSON response object retrieved by [AFNetworking](http://afnetworking.com/ "AFNetworking"). All of a sudden, I found that is a ridiculously diabolical mistake.

![AFNetworking](/assets/AFNetworkingHero.jpg)


This is what I use to call:

```swift
// AFHTTPSessionManager instance
manager.GET("domains", parameters: nil,
        success: {(task: NSURLSessionDataTask!, response: AnyObject!) in
            // How do I proceed with this F**KING response object???
        }, failure: {(task: NSURLSessionDataTask!, error: NSError!) in
            println("ERROR: " + error.localizedDescription)
})
```

I have to admit that I've done pretty stupid things like try parsing the *response.description* String into Dictionary using *NSJSONSerialization* blah blah blah, hmmm....as you could expect.

OK, the pitfall is clear and loud, the point is, I've totally forgotten that I'm using [AFNetworking](http://afnetworking.com/ "AFNetworking"), and **IT IS A Objective-C LIBRARY**, which obvioulsy will returns a Objective-C object, and in this case, it's naturally a *NSDictionary* instance. So it turns out that, I actually can use the *response* object directly just like I use regular *NSDictionary* object in Objective-C before.

![WTF](/assets/dude_wtf1.png)
