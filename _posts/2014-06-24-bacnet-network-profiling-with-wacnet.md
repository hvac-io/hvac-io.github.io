---
layout: post
title: "BACnet Network Profiling with Wacnet"
author: CF
description: ""
category: 
tags: []
---
{% include JB/setup %}

One of the most underused Wacnet feature is the REPL, which gives
access to a complete programming environment. I suppose this shouldn't
be surprising, as learning a new language is always a time consuming
endeavour.

![Wacnet REPL](/images/wacnet-repl.png "Wacnet REPL")

However, one can easily share little snippets to be used in the REPL.
The following code will export a text file containing a rudimentary
profile of the BACnet network.

{% highlight clojure %}
(->> (pmap #(try (remote-object-properties % [:device %] [:model-name :object-name :vendor-name])
                 (catch Exception e))
           (remote-devices))
     (apply concat)
     ((fn [x] (with-out-str (print-table x))))
     (spit "network-profile.txt"))
{% endhighlight %}

And when we open the `network-profile.txt` file:

    | :vendor-name             | :object-name                            | :model-name                      | :object-identifier |
    |--------------------------+-----------------------------------------+----------------------------------+--------------------|
    | ABB                      | DRIVE_U1_V_ALI                          | ACH550                           | [:device 50401]    |
    | ABB                      | DRIVE_U1_V_RET                          | ACH550                           | [:device 50402]    |
    | ABB                      | UV01_DRIVE_ALIM                         | ACH550                           | [:device 110201]   |
    | ABB                      | UV01_DRIVE_RET                          | ACH550                           | [:device 110202]   |
    | TELEMECANIQUE            | ATV 61                                  | ATV61HD15Y                       | [:device 110004]   |
    | TELEMECANIQUE            | ATV 61                                  | ATV61HD15Y                       | [:device 110005]   |
    | CARRIER                  | CHILLER                                 | BACnet Local Equipment Interface | [:device 50300]    |
    | Delta Controls           | UV20                                    | DAC_1180                         | [:device 10301]    |
    | Delta Controls           | AC25                                    | DAC_1180                         | [:device 10401]    |
    ...
    (about a hundred more)

Neat, right?
With a few lines of code, you generated a summary of all
the devices, their model and from which vendor they originate.
