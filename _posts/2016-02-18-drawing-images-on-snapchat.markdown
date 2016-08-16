---
title: "Automated drawing of Snapchat snapsterpieces"
date:   2016-02-18 7:16:00
description: A talk about the tech behind Snart
layout: post
---

Recently I released my application 'Snart' as well as a UI to accompany it. While developing the UI I had to consider to myself the audience
of whom I wanted to use my applicaiton, and reseted on the ideal person as someone who has an advanced experience with computers and is comfortable
running and using hacky applications (After all Snart is pretty weird)

## Interpreting Images
Snapchat does support mutliple colors, however for the sake of simplicity, I made Snart only draw in binary (either with color or without).
Snart could have multi-color support in the future, but there are just too many calculations and things I have to account for to make this
possible. Snart uses an older Java OpenCV binding (JavaCV, which I will NEVER use again for the sake of how little documentation there is on it
), seperates the colored pixels from the opaque and white background, and records them into a collection. Then when the entire image is processed it 
is prepared for execution.

## Sending Touches
This was not a particularly challenging problem, after all the Android Debug Bridge (ADB) supports this by default with a command of the format
adb shell swipe/touch <x1> <y1> <x2> <y2>. Initially I used an a touch based implementation, sending 1 tap per pixel. However since ADB requires
a response from the phone after sending requests, taping once pixel per ever 2-ish seconds would take a ludicrous amount of time. So I implemented a swipe implementation.

What the swipe implementation does is record an enitre list of pixels that are all colored/black in between the white/background pixels. Then
When this chain is broken, either by a new line or by a white pixel then the list is dumped, and the first and last pixels are used as 
starting and ending points for the swipe. This sped the process up significantly, however it could be sped up faster by convincing ADB to use
UDP packets (somehow).

## Steps from the End
If you look at the history of the repository, you'll notice that originally Snart was going to have its own file type. However because of
the need of a compression method as well as the fact that reading and expanding a file could severely affect load times. But from here on out Snart
is a dead-ish project. I won't be updating it unless popularity grows, or someone else takes interest in maintaining it. If this sounds like
you contact me at andros.cyang@gmail.com


