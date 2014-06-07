---
layout: post
title: "Getting BACnet Data Through a Firewall"
author: CF
description: ""
category: 
tags: []
---
{% include JB/setup %}


One of the network components often out of the reach of the controls
technician is the firewall. While one can easily build a BACnet
network without any interaction with the IT department, the firewall
is another story. It prevents communication with the outside world,
immediately shutting down any hope of remote monitoring.

Aware of this difficulty, we decided to focus on the problem and came
up with a simple plug and play solution.

## How Does it Work?
Firewalls usually follow a simple rule: let the communication from
inside out, but *don't* let any exterior communication get in, unless
it's in response to a previous inside communication.

This means that if I'm inside the firewall, I can browse the Internet
from my workstation, but someone outside the firewall can't
connect and check something like a control network.

It's a simple, and yet quite effective rule that keeps most of the bad
guys outside.

The usual way to access the control network from outside is to add a
special exception into the firewall. This exception says "ok, don't
let anyone enter, *except* this guy." While it's a valid solution, it
can be quite time consuming and is often the responsibility of a
completely different department. (We love you IT guys, but sometimes
you are hard to get!)

Each time you make a hole like this one in a firewall,
you add an additional attack vector. Trusted 3rd parties allowed to
have their own hole are few and far betweens.

![Firewall](/images/firewall.jpg "Firewall")

## The Control Network: A Security Risk

By letting someone access the control network, you potentially risk
much more than just the control network. Many enterprises don't have
their control network completely separated from their normal
day-to-day network. This means that by connecting to a BACnet device,
I could have access to all the computers on the network and wreak
havoc on all the machines, or simply get my hand on juicy trade
secrets.

The control network is the mother of all backdoors. Nobody thinks
about it, but it's there and have all the network capabilities a
hacker could hope for. Sure, BACnet devices shouldn't let me access
the network like this, but devices can be hacked. Especially devices
built from the ground up with microcontrollers where security is an
after-thought.

By the way, some people directly expose their BACnet port (47808) to
the Internet. **DON'T DO IT!** I exposed mine a few days ago to see if
a fish would come up. Within 3 hours someone was fursiously sending
BACnet packets to it. An attempted
[buffer overflow](http://en.wikipedia.org/wiki/Buffer_overflow)?

![Exposed BACnet Port](/images/expose-bacnet.jpg "Exposed BACnet port")


## How Vigilia Gets the BACnet Data Through (almost) any Firewall

Obviously, we don't ask our customers to expose their BACnet port.
Furthermore, the hole-in-the-firewall solution was too complicated and
too 'custom' for us. (Every single enterprise seems to have a
different security policy and many hoops to go through.) We needed
something *very* simple and as much *plug and play* as possible.

We finally found a viable alternative. We think many others could
benefit from this little tip, so we give it away for free. Our (not so
secret) secret: We don't fight the firewall. We don't try to reach the
BACnet network from far away. We send the data *from inside* the
network.

That's right, we play with the rules of the firewall. We explained
earlier how the communication from the inside can go through without
any interference. That's the behavior we leverage.

We install [Wacnet](https://hvac.io/docs/wacnet), or even
simpler, plug in the [MicroB](https://hvac.io/products/microb), and
let them send us the required data.

The connection between the logging device and our servers are always
initiated from within. In fact, for those concerned about security,
*it's impossible for us to connect to our logging device from outside
your network*.

Granted, this won't work for someone wanting to send commands to the
control network. If you need this kind of capabilities, then you
really should deal with the IT departement. They'll be able to build
you a secure VLAN or something similar. But if you need monitoring and
logging, our solution is as simple as it gets.
