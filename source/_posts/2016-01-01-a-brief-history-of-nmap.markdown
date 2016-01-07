---
layout: post
title: "A Brief History of NMap"
date: 2016-01-01 09:31:35 -0500
comments: true
categories: 
---

NMap. What is it? Where did it come from? Who wrote it? And why is it so many movies? 

I am approaching this as someone who is obviously learning about NMap (and the concept of scanning in general) for the first time, but as a result I hope this post functions as a completely basic introduction to the tool and the techniques for network scanning that it provides.

Note: For easy installation of Nmap on Mac, go to https://nmap.org/book/inst-macosx.html and download and run the .dmg file.

WHAT IS NMAP?
-------------

NMap is short for Network Mapper. It is essentially a toolbelt full of functionality that allows you to perform network scans. It was designed with the intent of quickly scanning large networks, although you can easily implement it to get information about a single host or target. You can use it to fulfill a wide variety of tasks, including security scans, figure out the services a host is running, "fingerprint" the operating system and applications on a host, the type of firewall a host is using, or do an inventory of a local network. In other words, Nmap can tell you what computers are currently connected to your local network, and target certain computers to provide you with a lot of information about them. Nmap has the ability to scan huge networks the serve hundreds of thousands of computers, or you can scan your family's computers when you're connected to your WiFi network at home. It can be used for good, or for evil. Nmap is one of the best ways for malicious hackers to determine what ports are open on a system, but it also works great for ethical hacking, in terms of discovering 'unlocked doors' or security flaws on a network and finding ways to properly address those vulnerabilities. 

So what exactly is scanning, you might ask. Scanning is a method for discovering 'exploitable communication channels', by sending out probes to as many listeners as possible, and then keeping track of ones that are receptive and useful to your purposes. Nmap provides a number of techniques to determine what ports of a host are listening for connections. A good analogy is the concept of massive telemarketing or snail mail campaigns for advertising purposes. You send a brochure or place a phone call to literally every number or address you have. If there is no response, you continue on to the next one. But the people who answer the phone, or reply to your brochure - you keep track of those responses and gather information on them. 

Nmap works by sending specially crafted data packets to ports, and analyzing the responses from ones that are open. A port is just an entry point to a network server. A port is associated with an IP address (of the host computer). You might have run into port conflicts before, when trying to run an app on your local computer. If a port is already in use, you'll get an error if you try to run something else on the same one, since only one process can bind to a specific IP address and port combination using. A port conflict is when multiple programs attempt to bind to the same port numbers on the same IP address using the same transport protocol. When use Nmap to do port scanning, we are attempting to connect to a range of ports in sequence on a single computer. This is the main way that network admins look for possible vulnerabilities to prevent malicious attacks, and it is also the way that evil hackers attempt to perform such attacks.

A host is a computer or other device connected to a computer network.

So what is an example of Nmap usage that will make some sort of sense to a noob like me? 

Well, when we're using Nmap from the command line, the basic syntax of a command looks like this:

$ nmap <scan type> <options> <target>

Everything that isn't an option or an option argument is treated as a specification for the target host. The simplest way to specify a target is by typing in the target's IP address or hostname for scanning.

So maybe I want to see some information about the router that is running the wifi network at my parents' house. I want to see what it says about its operating system. I can go ahead and type:

sudo nmap -O target.host.com

I have to use sudo because nmap requires root privileges, which sudo lets me use. (Even though I'm logged in as admin on my computer, I need to be the 'root user' to perform this nmap scan. Sudo will ask me for my laptop password when I hit enter).







