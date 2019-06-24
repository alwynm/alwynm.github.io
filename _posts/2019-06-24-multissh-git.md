---
layout: post
title: Setting multiple git repo with ssh key
categories: Cheatsheet
ready : true
---

### Creating a new SSH key

We will be needing two keys. Type the following in terminal to genrate a SSH key.

{% highlight js %}ssh-keygen -t rsa -b 4096 -C "your-email@example.com" 
{% endhighlight %}

This will prompt you to enter file in which to save the key. Repeat this twice. Note the give different name according to your convenience to identity each key for your repo. Lets say you named keys as:

1. repo1key
2. repo2key

### Registering your new SSH key

{% highlight js %}eval "$(ssh-agent -s)"
{% endhighlight %}

{% highlight js %}ssh-add ~/.ssh/repo1key
ssh-add ~/.ssh/repo2key
{% endhighlight %}

### Deploy your key to Github

Setting -> Deploy keys -> Add deply key <br />

Enter title and copy paste the content of the public key generated at `~/.ssh/` to key field. Click Add key. <br />
Repeat this same step to add public key on the other repo too. Public keys will have extenstion `.pub`, your corresonding public keys will be `repo1key.pub` and `repo2key.pub`.

### Create a git config file

{% highlight js %}ssh-add ~/.ssh/config
{% endhighlight %}

Here is an example for your `~/.ssh/config` file

{% highlight js %
Host repo1.github.com
HostName github.com 
IdentityFile /home/yourname/.ssh/repo1key
IdentitiesOnly yes

Host repo2.github.com
HostName github.com 
IdentityFile /home/yourname/.ssh/repo2key
IdentitiesOnly yes
{% endhighlight %}

These four line entry will differ for each repo you want to setup.

### Clone repo

Get the `Clone with SSH` url, it will look like:

{% highlight js %}git@github.com@yourgitname/repo1.git
{% endhighlight %}

This url can be used for standard SSH key but as we have defined two different `Host` in  `~/.ssh/config` file, you should use the following.


{% highlight js %}git@repo1.github.com@yourgitname/repo1.git
git@repo2.github.com@yourgitname/repo1.git
{% endhighlight %}

Now you can clone your repos

{% highlight js %}git clone git@repo1.github.com@yourgitname/repo1.git
git clone git@repo2.github.com@yourgitname/repo1.git
{% endhighlight %}

