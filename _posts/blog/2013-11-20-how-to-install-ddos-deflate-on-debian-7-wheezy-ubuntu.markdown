---
layout: post
title: "How to install (D)DoS Deflate on Debian 7 (Wheezy) / Ubuntu"
description: Installing (D)DoS Deflate on Debian 7 (Wheezy) / Ubuntu on Linux server (or VPS). How I managed to install and configure it successfully on my machine.
date: 2013-11-20 16:54:46
author: Bestbg
categories:
- blog
- technical-tutorials
img: DDoS-Deflate.jpg
thumb: DDoS-Deflate-thumb.jpg
tags: [ddos-deflate, debian, servers, ubuntu]
---

There are many guides about how to install **(D)DoS Deflate** on Linux server (or VPS) and in most cases there shouldn't be a problem with it but I faced some small issues installing (D)DoS Deflate on **Debian 7 (Wheezy)** so I decided to share how I managed to install and configure it successfully on my machine.
I guess the same fix (see below) would work on Ubuntu as well.

Install (D)DoS Deflate the way it is advised on their [**official website**](http://deflate.medialayer.com/) or follow these steps:
<br /> <!--more-->
{% highlight ruby linenos %}
cd /usr/local/src/
sudo mkdir ddos

cd ddos

sudo wget http://www.inetbase.com/scripts/ddos/install.sh

sudo sh install.sh
{% endhighlight %}
(* If you have root access you don't need to use sudo)

<center><script type="text/javascript">
ad_idzone = "1089632";
ad_width = "468";
ad_height = "60";
</script>
<script type="text/javascript" src="https://ads.exoclick.com/ads.js"></script>
<noscript><a href="http://main.exoclick.com/img-click.php?idzone=1089632" target="_blank"><img src="https://syndication.exoclick.com/ads-iframe-display.php?idzone=1089632&output=img&type=468x60" width="468" height="60"></a></noscript></center>

When the installation is done you will see something like this:
{% highlight ruby linenos %}
Installation has completed. Config file is at /usr/local/ddos/ddos.conf
Please send in your comments and/or suggestions to email@vsnl.com
{% endhighlight %}

Edit the configuration file depending on your requirements:
{% highlight ruby linenos %}
sudo nano /usr/local/ddos/ddos.conf
{% endhighlight %}

You may also want to **white list** your IP address:
{% highlight ruby linenos %}
sudo nano /usr/local/ddos/ignore.ip.list
{% endhighlight %}

Now it is a time to run (D)DoS Deflate:
{% highlight ruby linenos %}
sudo /usr/local/ddos/ddos.sh -c
{% endhighlight %}

Unfortunately I got this:
{% highlight ruby linenos %}
/usr/local/ddos/ddos.sh: 13: [: /usr/local/ddos/ddos.conf: unexpected operator DDoS-Deflate version 0.6
Copyright (C) 2005, Zaf email@vsnl.com
$CONF not found.
{% endhighlight %}

To fix this **open ddos.sh**:
{% highlight ruby linenos %}
sudo nano /usr/local/ddos/ddos.sh
{% endhighlight %}

and change the first line of the file from
{% highlight ruby linenos %}
!/bin/sh
{% endhighlight %}
to
{% highlight ruby linenos %}
!/bin/bash
{% endhighlight %}

There are at least two more instances of the same path in ddos.sh, so find them and change to **/bin/bash**
Save and close *ddos.sh*.

Start the service again:
{% highlight ruby linenos %}
sudo /usr/local/ddos/ddos.sh -c
{% endhighlight %}

If you get the following error message:
{% highlight ruby linenos %}
crond: unrecognized service
{% endhighlight %}

Open **ddos.sh** again:
{% highlight ruby linenos %}
sudo nano /usr/local/ddos/ddos.sh
{% endhighlight %}

Find "**add to cron**" part and change
_service crond restart_
to
_service **cron** restart_

(I found two instances that need to be changed).

Save, exit and start the service again:
{% highlight ruby linenos %}
sudo /usr/local/ddos/ddos.sh -c
{% endhighlight %}

If you did everything correct you should see the following message:
{% highlight ruby linenos %}
[ ok ] Restarting periodic command scheduler: cron [....] Stopping periodic command scheduler: cron.
{% endhighlight %}

We are done.

<center><script type="text/javascript">
ad_idzone = "1089632";
ad_width = "468";
ad_height = "60";
</script>
<script type="text/javascript" src="https://ads.exoclick.com/ads.js"></script>
<noscript><a href="http://main.exoclick.com/img-click.php?idzone=1089632" target="_blank"><img src="https://syndication.exoclick.com/ads-iframe-display.php?idzone=1089632&output=img&type=468x60" width="468" height="60"></a></noscript></center>

**Note:** I read in few forums/blogs that there is a bug with (D)DoS Deflate version 6.0 and to fix it you need to open **/usr/local/ddos/ddos.sh** and replace:
{% highlight ruby linenos %}
netstat -ntu | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -n
{% endhighlight %}
with
{% highlight ruby linenos %}
netstat -ntu | grep ‘:’ | awk ‘{print $5}’ | sed ‘s/::ffff://’ | cut -f1 -d ‘:’ | sort | uniq -c | sort -nr &gt; $BAD_IP_LIST
{% endhighlight %}

I didn't have possibility to test it so it is up to you to make this change or not.

Hope the article was helpful to some of you.
If you have something to add or find mistakes please let me know by commenting.
