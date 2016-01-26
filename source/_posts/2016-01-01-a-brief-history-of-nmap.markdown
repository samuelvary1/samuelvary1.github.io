---
layout: post
title: "A Brief Intro to Nmap"
date: 2016-01-01 09:31:35 -0500
comments: true
categories: 
---

Nmap. What is it? Where did it come from? Who wrote it? And why is it so many movies? 

I am approaching this as someone who is obviously learning about Nmap (and the concept of scanning in general) for the first time, but as a result I hope this post functions as a completely basic introduction to the tool and the techniques for network scanning that it provides.

Note: For easy installation of Nmap on Mac, go to https://Nmap.org/book/inst-macosx.html and download and run the .dmg file.

WHAT IS NMAP?
-------------

Nmap is short for Network Mapper. It is essentially a toolbelt full of functionality that allows you to perform network scans. It was designed with the intent of quickly scanning large networks - picture using Nmap to scan hundreds of thousands of computers connected to the same network - or you can use it to gather information on only a few target computers. 

When most programmers hear the term Nmap, they immediately think of a tool for scanning servers and finding which ports are open, and subsequently attacking them. But Nmap can be used for good just as effectively as it can be used for evil.

{% img center http://25.media.tumblr.com/tumblr_m3bqcrcAaF1qabfx1o2_500.gif %} 

Nmap is able to fulfill a variety of tasks, including security scans, figure out the services a host is running, "fingerprinting" the operating system and applications on a host, the type of firewall a host is using, or do an inventory of a local network. As I mentioned, it is one of the best ways for malicious hackers to determine what ports are open on a system, but it also works great for ethical hacking, in terms of discovering 'unlocked doors' or security flaws on a network and finding ways to properly address those vulnerabilities. Different tasks require different permissions, and I've read about Nmap being likened to a box of dynamite - it's incredibly powerful, but if you don't know what you're doing you can blow your foot off. 

{% img center http://www.filmfodder.com/tv/lost/archives/Lost_Arzt.jpg %}


You can't run around scannin' everything you dang please! Security professionals will not appreciate your unauthorized probings of their networks. However, if you have permission, and you know what you're doing, Nmap has the ability to scan huge networks the serve hundreds of thousands of computers, or you can scan your family's computers when you're connected to your WiFi network at home. 

Nmap works by sending specially crafted data packets to ports, and analyzing the responses from ones that are open. The metaphor I came across most frequently is that it's like sending out mass mailers to customers. You place a brochure in every mailbox in the neighborhood, and most people ignore it (closed ports). However, a few people reply to the brochure, and you can then analyze their responses and pay special attention to those, and just forget about the people who ignored your attempts to reach out.

Who invented it?
----------------
{% img center https://pbs.twimg.com/profile_images/1360368660/Defcon18-Fyodor-Presenting-573x573.jpg %}

This is Gordon Lyon, the inventor of Nmap. He's pretty smart. He often operates online under the alias of Fyodor Vaskovich, in honor of Dostoevsky, and he's incredibly active in the ethical hacking community even to this day. He released Nmap (open source of course) in 1997, and has spent the past couple of decades developing it and other security-related projects. He even wrote a thriller novel with highly accurate depictions of hacking, and appeared in a comic book where he saves a kidnapped Nmap developer from a criminal organization that was intent on forcing him to hack for evil. 

{% img center http://fpix.us/pics_me/clustermind_pp44.jpg %}

Lastly, one of the coolest things about Nmap is the number of movies it has appeared in. As Steven mentioned when he gave us a brief intro to Nmap, at some point Hollywood and other film industries decided Nmap was the most hacker-like thing they could put on screen to give the movie that touch of realism, and they're not wrong. 

Possibly the most famous example comes from the Matrix Reloaded, where Trinity uses Nmap to find a vulnerable SSH server to hack the city power grid and help Neo out. She even uses a realworld loophole to exploit the server. 

{% img center http://linuxzone.es/app/uploads/2011/08/matrix-linux.png%}

You can check out the other movies it has appeared in here, and generally learn more about Nmap on its official site, www.nmap.org.  
