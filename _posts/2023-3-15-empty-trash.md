---
layout: post
title: Auto emptying trash in Ubuntu
categories: General
ready : true
---

[trash-cli](https://github.com/andreafrancia/trash-cli) trashes files recording the original path, deletion date, and
permissions. It uses the same trashcan used by KDE, GNOME, and XFCE, but you can invoke it from the command line (and
scripts). Install `trash-cli` with the below command:

{% highlight js %}
sudo apt install trash-cli
{% endhighlight %}

Run `trash-empty 30` to remove all files from trash which are older than 30 days (You can change this number as you
like). To automate this, add a command to Startup Applications:

<p align="center">
  <img src="https://i.stack.imgur.com/trlEx.png" alt="Ubuntu startup application">
</p>

If you rarely restart your system, use `cronjob`. You can install `cronjob` with `sudo apt install cron` and edit/create
your own crontab file with `corntab -e` and add the below 

{% highlight js %}
0 0 * * * trash-empty 30
{% endhighlight %}

Source: [askubuntu](https://askubuntu.com/a/144963/667206)


