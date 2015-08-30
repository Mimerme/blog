---
title:  "YakHax Moving Forward"
date:   2015-08-29 10:37:00
description: Getting over the hurdles associated with opening the Yik-Yak API to the public
layout: post
---

With the YakHax library nearly completed over these past 3 months and summer nearing its end
I believe it is appropriate for another post and a few topics associated with the development
of the YakHax. This post is aimed for non-tech geeks and just people who are interested in a nice read

## Preventing API abuse
One important idea when developing the library was how to prevent abuse. This is to maintain a positive image with Yik Yak.
I would much rather not have Yik Yak get mad over someone abusing the API for malicious purposes. However there are already existing libaries in other
languages, but their problem is that they require a hard coded value to actually allow the library user to utilize them by encoding messages. Without
this value all requests would not be accepted by Yik Yak. In most third party libraries it is called a API key. The
key is not something a normal joe-schmo would be able to find in a few minutes, and would require a bit of reverse engineering. However thanks to
the members of the Yik Yak hacking community I was able to obtain this key and create a server, that when feed the message to be encoded
would use this key and return the proper encoded message.

## Network Interface
When designing the library I made the decision to create YakHax as a network interface rather than a full on API that parses the output, which is most times in JSON format. This cut back on a lot of the code I would have to write and simplified my task, while allowing users to customize how they wanted to use the API. Also  because Yik Yak often tended to change a lot of their output from requests throughout updates, which would make keeping the library up to date much
harder. I will probably release another library to parse the output instead though, but no promises on keeping it up to date

## Third party tools and libraries
Tools used specifically included Charles and Fiddler, Charles to intercept requests from my Android device and Fiddler to review my requests send by my library. To manage the project I used Maven to sort my dependencies/third party libraries. Third party libraries included JSoup and Apache HTTP Commons. Both of these libaries allow my program to more easily send requests. JSoup is much easier but is missing some features that I included with Apache HTTP Commons.

## Debugging the Application
YikYak sends its requests through HTTPS to protect against Man in the Middle attacks, which made a lot of tools, for intercepting the requests to debug them, useless. Thus I used Charles for this task. Routing the requests on my Android device to my PC through a proxy by installing a security certificate, made my job much easier. Fiddler was also a very good tool especially when debugging my library to make sure the proper requests were being made because JSoup made very weird requests often times with random headers that I did not need.

## Android vs iOS
On the surface one could tell the UI differences from the YikYak Android app vs iOS app. But underlying there are also a few differences in the request. The API key I was talking about earlier is different between the iOS and Android applications. The Android key looks similar to an MD5 hash, while the iOS key contains dashes. I chose to debug and decompile the Android application because I did not have a jailbroken device accessible and had much more familiarity with Android app development. As far as I know the Android app generates the key from its package signature and encodes that value as well to generate the key. The User-Agents when sending requests differ with Android labeling itself as 'Android' and iOS labeling itself differently

## Rest in pieces Yodel
For those unaware of Yodel, like many other Windows Phone apps out there, was a third-party app that tried its best to emulate to emulate the official Yik Yak app because Yik Yak had not released a Windows Phone app. However since the app grew in popularity Yik Yak had recently sent a cease and desist letter to Soren21, the creator. It was honestly such a shame because 1) he had put a lot of effort, one could consider himself one of the pioneers for reverse engineering the Yik Yak API
and 2) a lot of people were basing their of library off of his JavaScript library because it was very well made. When his repository was finally taken down and replaced with a simple cease and desist it made me resentful at Yik Yak and the type of company it was running, preventing unofficial apps to cover what they themselves were too lazy to do. However rumors are in the air that they will release a third party API for developers as well as release a Windows Phone app, but still they remain only rumors.
