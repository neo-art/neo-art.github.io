---
layout: post
title: "Monetizing your Ghost blog"
date: 2013-11-25 01:22:46
author: Bestbg
categories:
- blog
- Ghost Blogging
- wordpress
img: Monetizing-your-Ghost-blog.jpg
thumb: Monetizing-your-Ghost-blog-thumb.jpg
tags: [ghost-ads, adsense, ghost, infolinks, monetize]
---
<center><a target="_blank" href="http://www.exoclick.com/?login=artv" rel="nofollow" title="Monetize All your traffic"><img src="http://www.exoclick.com/banners/468x60.gif" border="0" width="468" height="60" alt="Monetize All your traffic"></a></center>

Monetizing Your Ghost blog with [**Infolinks**](http://bit.ly/1c5aN2i){:rel="nofollow"}{:target="_blank"}{:title="Infolinks"} is a very simple process that takes no more than 2 minutes.
I used **Infolinks** for this example because most of my sites convert better with them but you can use the same method to integrate Google AdSense.

So let's start... If you still don't have an account with infolinks follow the link and sign up for their publishers program : [**www.infolinks.com**](http://bit.ly/1c5aN2i){:rel="nofollow"}{:target="_blank"}{:title="Infolinks"}.
The approval process usually takes not more than 24 hours. After receiving an email confirmation that your account has been approved login in your Infolinks account and visit the dashboard. Check if you need to amend your account or website data (add a new website if you need to) and go to "**Integrate**" tab.<br /> <!--more-->
Next "**Choose a website**" from the drop down menu (*choose your Ghost website*) and "**Choose your platform**". In our case we are going to choose "**JavaScript
(Any Platform)**".
Copy the code provided in your editor or just in Notepad.

<center><script type="text/javascript">
ad_idzone = "1089632";
ad_width = "468";
ad_height = "60";
</script>
<script type="text/javascript" src="https://ads.exoclick.com/ads.js"></script>
<noscript><a href="http://main.exoclick.com/img-click.php?idzone=1089632" target="_blank"><img src="https://syndication.exoclick.com/ads-iframe-display.php?idzone=1089632&output=img&type=468x60" width="468" height="60"></a></noscript></center>

Next go to your **Ghost installation** and find your active theme folder. In this example I used the default
Ghost theme "*Casper*". The files of the theme are located in
{% highlight html linenos %}
your_ghost_install/content/themes/casper
{% endhighlight %}

Open the file `default.hbs` and scroll down to find the `</body>` tag.
Paste the **Infolinks javascript code** just before the `</body>` tag.
Save and re-upload (if you are using FTP) the `default.hbs` to your **active theme folder**.
**Restart Ghost** to make sure that the change is live and you are done. Your [**Infolinks ads**](http://bit.ly/1c5aN2i){:rel="nofollow"}{:target="_blank"}{:title="Infolinks ads"} should appear on your blog almost immediately and your blog can start earning some money.

Hope you find this post useful and please leave a comment if you have any questions or simply want to add something.

Enjoy blogging with **Ghost** and check here for future posts that will help improve your Ghost experience and for more ways to monetize your blog as well.