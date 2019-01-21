---
layout: page
title: Working with Git
---

Copy git repository
{% highlight js %}git clone <url>
{% endhighlight %}

Create a new local repository
{% highlight js %}git init
{% endhighlight %}

Add one or more files to staging
{% highlight js %}git add <filename>
git add *
{% endhighlight %}

Commit changes to head (but not yet to the remote repository)
{% highlight js %}git commit -m "Commit message"
{% endhighlight %}

Send changes to the master branch of your remote repository
{% highlight js %}git push origin master
{% endhighlight %}

List the files you've changed and those you still need to add or commit
{% highlight js %}git status
{% endhighlight %}

Create a new branch and switch to it
{% highlight js %}git checkout -b <branchname>
{% endhighlight %}

Switch from one branch to another
{% highlight js %}git checkout <branchname>
{% endhighlight %}

List all the branches in your repo, and also tell you what branch you're currently in
{% highlight js %}git branch
{% endhighlight %}

Delete the feature branch
{% highlight js %}git branch -d <branchname>
{% endhighlight %}

Push the branch to your remote repository, so others can use it
{% highlight js %}git push origin <branchname>
{% endhighlight %}

Delete a branch on your remote repository
{% highlight js %}git push origin :<branchname>
{% endhighlight %}

Fetch and merge changes on the remote server to your working directory
{% highlight js %}git pull
{% endhighlight %}