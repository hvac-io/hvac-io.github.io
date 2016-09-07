---
layout: post
title: "Fun With Vigilia's API"
author: CF
description: ""
category: 
tags: [Vigilia]
---
{% include JB/setup %}

In the beginning, you created a Vigilia project.

Then you stayed in awe when you saw how you could manipulate the
recorded data at the speed of thoughts.

![Vigilia - Analyse](/images/vigilia-api/vigilia-analyse.gif "Vigilia - Analyse")

And now you're wondering if you can push things even further.

Well yes, you can!


# APIs Are for Machines... and Humans!

Vigilia's API was built using the Swagger framework. Was does it mean?
For the end user, it means you can test every endpoint directly from
your browser.

Give it a try! Go
[there](https://vigilia.hvac.io/api/v1),
you should see what is shown in the picture below.

[![Vigilia - HVAC-wiki](/images/vigilia-api/swagger.png)](/images/vigilia-api/swagger.png)

Now, enter the test project ID (5371147be4b0222b740851a2) into the
project-id field and click "Try it out".

You will see what data the API is sending back.

[![Vigilia - HVAC-wiki](/images/vigilia-api/swagger2.png)](/images/vigilia-api/swagger2.png)

It’s pretty neat, eh!


## Follow the Links

While most APIs will return raw JSON data, we made sure to offer a
human readable version of our API. This means that if a browser ask
the API for some data, it will be returned in a (relatively) nice HTML
page. This page will then offer links that can show you even more
data...

Try it. You can start from the
[project root](https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2),
and follow the links all the way down to individual objects! No
documentation needed, just links!


# An Example Application

Ok, so the API is all nice and shiny, but what can you do with it?

Let's say I want my desktop to warn me if a value from an object is
above a given threshold.

I'm using Ubuntu, so we'll go with that, but the principle on Windows
would be the same.

In my example, I want to know when the object
[SY-1AR T-ALIM](https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2/devices/10122/objects/0.2)
has a temperature higher than 10°C.

We can retrieve the JSON data using *curl*:

{% highlight Bash shell script %}
curl -H "Accept: application/json" https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2/devices/10122/objects/0.2
{% endhighlight %}

This is the data we'll get:

{% highlight javascript %}
{
  "project-id": "5371147be4b0222b740851a2",
  "device-id": "10122",
  "object-type": "0",
  "object-instance": "2",
  "description": "",
  "object-id": "0.2",
  "status-flags": {
    "overridden": false,
    "out-of-service": false,
    "fault": false,
    "in-alarm": false
  },
  "present-value": 17.64428,
  "timeseries": {
    "href": "https://vigilia.hvac.io/api/v1/timeseries?global-object-ids=5371147be4b0222b740851a2.10122.0.2"
  },
  "last-update": "2014-02-12T23:39:24.519Z",
  "object-name": "SY-1AR T-ALIM",
  "units": "degrees celsius",
  "global-id": "5371147be4b0222b740851a2.10122.0.2",
  "href": "https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2/devices/10122/objects/0.2"
}
{% endhighlight %}


The data we received is in JSON. If you want to easily handle it in
the shell script, I recommend installing [JQ](https://stedolan.github.io/jq/):

{% highlight Bash shell script %}
sudo apt-get install jq
{% endhighlight %}

Ok, back to our data. 
We can get the present value of our object with the 'present-value' field:

{% highlight Bash shell script %}
curl -H "Accept: application/json" https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2/devices/10122/objects/0.2 | jq '.["present-value"]'
{% endhighlight %}

In this case we get the value `17.64428`.

All that's left to do now is to compare it to our threshold and show a
warning message if we are above it:

{% highlight Bash shell script %}
pv=$(curl -H "Accept: application/json" https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2/devices/10122/objects/0.2 | jq '.["present-value"]'); if [[ $pv > 10 ]]; then notify-send "Present value is greater than 10!"; fi
{% endhighlight %}

![Vigilia - Desktop Alert](/images/vigilia-api/alert.png "Vigilia - Desktop Alert")

We can even add a little icon to make everything a little more professional:

{% highlight Bash shell script %}
pv=$(curl -H "Accept: application/json" https://vigilia.hvac.io/api/v1/project/5371147be4b0222b740851a2/devices/10122/objects/0.2 | jq '.["present-value"]'); if [[ $pv > 10 ]]; then notify-send -i ~/Vigilia-logo.png "Present value is greater than 10!"; fi
{% endhighlight %}

![Vigilia - Desktop Alert](/images/vigilia-api/alert2.png "Vigilia - Desktop Alert")

Sweet!

Now we could just add this script to a cron job and execute it every
hour. Instead of showing a message on the desktop, it could also send
an email or SMS. The only limit is your imagination at this point!

It is important to note that the main Vigilia
[interface](https://vigilia.hvac.io/v/5371147be4b0222b740851a2?bc%5B%5D=%253Aa10122..0.7..0.2..4.1#/devices/10122)
is built with this API. We don't keep secret resources to ourselves.
If you can see some information in the Vigilia interface, then you
know for sure it's available via the API and you can use it in your
own applications.
