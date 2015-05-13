---
layout: post
title: "Analysing Multi Stage Equipement with Virtual Objects"
author: CF
description: ""
category: 
tags: [Vigilia]
---
{% include JB/setup %}

One kind of system that was always a little 'delicate' to study is the
multi-stage system (especially with alternation). Unless those who
programmed the system were kind enough to create easy-to-use
variables, it's hard to quickly find out how many stages are active.

We recently had a system with 4 heat pumps, each with 2 stages, making
a total of 8 stages.

Here's what those stages look like in Vigilia's analysis tab:

![img](/images/multi-stage/individual-stages.png){: .well}

Sure, it's nice, you can see how each stage was used... but you can't
really tell WHEN most of them were active.

This is were virtual objects save the day.

You see, every stage is a binary value. On/off, or more precisely, 0
or 1 in Vigilia's recorded data. This means that we can use binary
values the same way we would use any other value (addition, multiplication...)

In this case, we take every single stage and add them up:
![img](/images/multi-stage/virtual-object-creation.png)



When we look back into our analysis tab, here's what we get:
![img](/images/multi-stage/stages-merged.png){: .well}




Much better, isn't it? Not only is it much easier on the eyes, but you
can now select "when we had more than 5 stages active" and see WHEN it
was happening.

![img](/images/multi-stage/stages-merged-filter.png){: .well}



Finding interesting things in a sea of data is all about making the
tools work for you. While we knew the virtual objects were going to be
powerful, this is the kind of thing that goes beyond our own
expectations.

If you have a system you'd like to try, go ahead! We offer 2 weeks of
[free trial](https://hvac.io/services/vigilia/pricing).


