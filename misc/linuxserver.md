---
layout: page
title: Working with remove server
---

Login server

{% highlight js %} 
ssh <user-name>@<ip>
{% endhighlight %}

Login server with graphic support

{% highlight js %} 
ssh -X <user-name>@<ip>
{% endhighlight %}

Copy files/folder to/from server

{% highlight js %} 
rcp -r <source/path/to/folder> <username>@<ip>:<path/to/folder>
{% endhighlight %}

Mount remote Linux filesystem

{% highlight js %} 
sudo apt-get install sshfs
sudo mkdir /mnt/server
sudo sshfs -o allow_other <user-name>:<path/to/home> /mnt/server
{% endhighlight %}
If Uduntu, go to "connect to server"
Server Address: {% highlight js %} sftp://<user-name>@<ip></ip></path/to/home> {% endhighlight %}

Explore server files in a window

{% highlight js %} 
xdg-open .
{% endhighlight %}