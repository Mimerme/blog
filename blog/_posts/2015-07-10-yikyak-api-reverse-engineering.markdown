---
title:  "Introduction to Reverse Engineering the Yik-Yak API"
date:   2015-07-10 01:10:00
description: The well needed step-by-step story on my journey to reverse engineer the Yik-Yak API
layout: post
---

For those who may not be as updated to the latest social media trends, Yik-Yak
is a new social media network that allows people to send 'anonymous' posts (in quotes
because it is well known that they collect device info/UUID and IP addresses),
and other people within the local area can view these posts using the
GMaps API. Meaning that those who are on your same college campus as you can see
your posts and you can see their posts. This allows for anonymous communications
between people with similar knowledge of the area rather than across the globe.
Of course just as Facebook was designed for an older audience but however gathered
a large younger audience, Yik-Yak is doing the same thing, attracting high school
and middle school students rather than just college students. This opens up the
entire community to cyber-bullying and gossip because people know other people.
Yik-Yak is aware of this problem and is also taking measures.

### Why do this?
Snapchat once had a very open API, that was well documented but was not made
official, but due to some third party apps causing chaos by stealing
images they quickly closed up the API to essentially make a PR statement
and put their iron fist down and removed many other third party Snapchat apps.
Yik-Yak too once had this problem, where everything was as simple as a REST API,
without any protection. Yik-Yak quickly fixed this and killed off the potential
abuse. I have always found an interest in social media and how it works, but
never have been fond of the practices that arise such as treating followers on
Instagram as a definition of popularity. Exposing these APIs would allow for
desktop apps and perhaps further extension of the first party applications.

### How will you do this?
I already have a GitHub repository setup for this and am using the wiki as a minor
blog such as day to day activities, and will use this blog as very important matters.
I will be writing the console application in Java and develop a Java wrapper for the Yik-Yak
API. I may provide and executable and jar download for those who may be interested.
A lot of progress has been made on the wiki so check that out if you are interested.
Of course this will not be my only project and I will work on this project for a
different taste every once and a while.
