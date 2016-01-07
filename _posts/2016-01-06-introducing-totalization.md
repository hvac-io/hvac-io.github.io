---
layout: post
title: "Introducing Totalization"
author: CF
description: ""
category: 
tags: [Vigilia, BACnet]
---
{% include JB/setup %}


I know what you are thinking... "Wait a minute, totalization is not a
new feature, I have an accumulator BACnet object in a device from 2004!"

While you'd be correct, this is not exactly the same kind of
totalization. The one we are introducing is much, MUCH more flexible.

## What Was Available

Prior to this day, you usually had 2 ways to get a total consumption
for a system. I'll quickly describe each of them and explain their disadvantages.

### Accumulator BACnet Object 

This object would take an input and count the number of time it pulsed.

![Bacnet Accumulator](/images/totalization/bacnet-accumulator.png "BACnet Accumulator")
*Bacnet Accumulator from the BACnet standard*

The accumulator needs to be correctly configured in order to show the
correct amount, but this is true of pretty much everything, so it's
not really a disadvantage. The real caviat is that you must be
absolutely certain that the pulsing equipment will not pulse faster
than the controller can read it.

Let me give you an example : If you have an input pulsing up to 10
times a second, but the controller can only read this input 2 times
per second, you **cannot** know how many times it pulsed. You are
completely blind and the value recorded will be worthless.



### Script Totalization

This is the poor man's accumulator. If you don't have an equipment
with a pulsing output to count the consumption, you can still
approximate it by taking the value every X amount of time and bringing
it back to a time unit.

Let's say I have an input giving me the power of a compressor.

Minute 1 : 100 kW
Minute 2 : 110 kW
Minute 3 : 109 kW

Each minute is 1/60 of the hour consumption. Our totalizer in kWh would look
something like this :


    Do Every 1 min
    total-consumption = total-consumption + (109kW * 1/60) kWh


(By the way, you can easily convert your units in Vigilia: simply use
a virtual object and apply the conversion equation.)



### Drawbacks

This script totalization, along with the BACnet accumulator, have a
huge drawback. What am I saying? A terrible, horrible, gigantic
drawback : They keep the state *inside* the controller. "What is the
problem with that?" you may ask. Well, if for any reason someone uploads an
old backup into the controller, the totalization is lost.

![Loading backups messes totalization](/images/totalization/totalization-kill.png "Loading backups messes totalization")
*Be afraid, very afraid*

You don't even have to load a backup to screw everything. Anyone with
an access to the BACnet network is able to change those values.


If you rely on any of these two types of totalizations, you should be
terrifed. You can lose months of data in an instant. 


Imagine this scenario : you are hired to make an energetic study based
on a year of observation. The first 12 months are there solely so you
can observe how the different systems are behaving. On the 11th month,
someone loads old backups into the devices. BAM! You just lost
everything, without any hope of getting this precious data back.


![Whyyyy](/images/totalization/whyyyy.jpg "Whyyyy")


Finally, You must also know *in advance* that you are going to need
it. 


Going back to the previous scenario, can you imagine realizing at the
10th month you forgot to record a crucial object? How are you going to
explain to your customer that you just wasted **months** because you
forgot something? Good luck keeping your professional image!


## Vigilia Totalization

Now it's time to talk about Vigilia's totalization feature and how we
learned from the industry's mistakes to make something greater.

### Tamperproof

Contrary to the methods we saw earlier, Vigilia does not store the
values inside the controllers. In fact, Vigilia never stores any
totalization anywhere, because they are always calculated on-the-fly
(just like
[virtual objects](http://blog.hvac.io/2015/03/11/introducing-virtual-objects/)).

By doing things this way, we are never at risk of having our precious
data tempered with.

You could reload the controllers backups every day and it would not
affect the results whatsoever.


### Backward Compatible Totalization

Because everything is calculated on-the-fly, *you don't need to create
totalization in advance*.

You'd like to know the energy consumption of a system you started
recording 5 months ago? No problem, just create a new totalization. It
will automatically use the data you already recorded.


### Filtered and Conditional Totalization

As previously mentioned, everything is calculated on-the-fly.
Everything is dynamic, ready to answer the questions you are asking
NOW.

One huge advantage of this is the ability of asking very precise
questions that appears only when you are in the middle of an analysis.

"What is the total consumption..."

- "... when the fan was working?"
- "... for the last 10 days, only between 2AM and 6AM?"
- "... when the outside temperature was below 0°C?"

If all you have is a BACnet accumulator, there's almost no way you can
answer those questions. On Vigilia, getting this kind of information
is as simple as dragging your mouse :

![Totalization update](/images/totalization/kwh-totalization.gif "Totalization update")

The recorded object is the power in **kW**. We convert it in **kWh** and show
it as the "sum-hours". Notice how every update is immediate.



## We Got Your Back

It's incredible how unforgiving the previous tools were.

You had to know *for sure* what information you would need many months
in advance. 

The data was fragile and unreliable. You had to cross your fingers
that it would still be there when you finally needed it.

You also needed to ask the right question from the start.
Forgot to filter out the data when the fan wasn't working? Too bad!


Man, that sucked. 



Fortunately, all of those problems are now solved with Vigilia.

You can create new totalizations months after your recorded the data.
It's no longer the end of the world if you forgot something.

The data is securely stored away, out of reach of anything that could
happen on your BACnet network. 

You can ask brand new questions and recalculate everything on-the-fly.


In case you have yet to install Vigilia on your network, take
advantage of the trial period and
[give it try](https://hvac.io/services/vigilia).
