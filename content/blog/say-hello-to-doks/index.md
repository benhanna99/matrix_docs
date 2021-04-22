---
title: "How Does the Internet Work?"
description: "Learn How The Internet Works"
lead: ""
date: 2021-02-04T09:19:42+01:00
lastmod: 2021-02-04T09:19:42+01:00
draft: false
weight: 50
images: ["say-hello-to-doks.png"]
contributors: ["John Doe"]
---

Whenever an email, webpage, tweet, image etc etc travel across the internet, computers break the information into smaller pieces called **packets**. When information reaches its destination, the packets are reassembled in its original order to make a email, webpage, tweet, image etc etc.

A server is a special computer connected **DIRECTLY** to the Internet. A website is files on that servers hard drive. So therefore a website exists on a computer, somewhere, and is accessed **through** the Internet.

## Internet Protocol (I.P Addresses)

Every server has a unique I.P address. An I.P address is like a postcode address. It helps servers find it each other. This could look something like **87.61.487.670** But since this doesn't look pretty we give them names like google.com.

A computer used at home is NOT a server as it is not connected *DIRECTLY* to the internet.Instead, these are called **CLIENTS** as they are **INDIRECTLY** connected to the internet via an (ISP) Internet Service Provider, such as Virgin. 

**EVERYTHING** connected to the internet has an I.P address. Everything connected to this I.P address has a mac address also.

At home, the I.P address will be for the modem/ gateway/ Router plugged into the coaxial cable provided by the ISP. An I.P is essentially the address of the modem/router. An I.P address is the internet address of the place of residence. 

Each individual device connected to this I.P address either wirelessly or via a cable will then have a **mac address**

## MAC Address

A mac address is the way the internet recognizes the address of individual devices connected to your router.
If you took your phone over to a friends house the I.P address would change but the MAC address would stay the same.

## Routers

Anywhere 2 or more pieces of the internet intersect, there is a piece of equipment called a router. Routers direct packets around the internet helping each packet get one step closer to its destination. Everytime you visit a website, upwards of 10 to 15 routers may help your packets make their way to or from your computer.

If you imagine each packet as a piece of candy wrapped in several layers:

The first layer is your computers I.P address. Your computer send the packet to the first Router which adds its own I.P address. Each time a packet visits a new router, another layer is added until it reaches the server. 

Then when the server send the information back, it creates packets with an identical wrapping. As a packet makes its way back to the correct computer, each router unwraps a layer to discover where to send the packet next.

