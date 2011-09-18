---
layout: post
title: Tomato Firmware
---

## Tomato Firmware

[Tomato firmware](http://www.polarcloud.com/tomato) is the successor to [DD-WRT](http://www.dd-wrt.com/) as the premier open source firewall. The active development for DD-WRT has stymied while Tomato contains the latest versions of Universal Plug N Play and Quality of Service features with a great user interface to boot. Running any network over 5 people, especially where bandwidth is limited, it is imperative to have these services to forward ports automatically and throttle bandwidth of lower priority traffic. Should one person decide they would like to torrent, that service can be classified, and capped appropiately. No longer will the Internet stop working as ACK packets fall to the floor. Below are the settings I use for a network of 30-50 people. Right off the bat it worked great from the setting found at Tomato USB. There are a few changes to include Battle.Net and SubSonic music streaming service.

I run [Toastman's](http://www.4shared.com/dir/v1BuINP3/Toastman_Builds.html) builds on an [ASUS NT-16](http://www.amazon.com/RT-N16-Wireless-N-Maximum-Performance-single/dp/B00387G6R8). Originally, I had used a [Linksys WRT-54GL](http://www.amazon.com/Cisco-Linksys-WRT54GL-Wireless-G-Broadband-Compatible/dp/B000BTL0OA/ref=sr_1_1?s=electronics&ie=UTF8&qid=1316375485&sr=1-1), but CPU load was consistently above .50 and RAM usage was always more than 80%. With the ASUS, load is closer to .10 and there is plenty of free RAM. However, I still use the WRT-54GL's for 3 wireless access points throughout the house that use the stable build of Tomato and pass all the work to the firewall.

