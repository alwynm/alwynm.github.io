---
layout: page
title: Anaconda commands
---

Download Anaconda from [here](https://www.anaconda.com/download/)

Create conda environment
{% highlight js %}conda create --name <env-name> python=<version-no.>
{% endhighlight %}

Activate conda environment
{% highlight js %}source activate <env-name>
{% endhighlight %}

Activate deconda environment
{% highlight js %}source deactivate <env-name>
{% endhighlight %}

List all conda environments
{% highlight js %}conda env list
{% endhighlight %}

Install packages in environment
{% highlight js %}conda install <package-name>
{% endhighlight %}

Remove packages from environment
{% highlight js %}conda remove <package-name>
{% endhighlight %}

List all packages in conda environment
{% highlight js %}conda list
{% endhighlight %}

Write all packages in an environment to a file
{% highlight js %}conda env export -f <file-name>.yml
{% endhighlight %}

Use above file to replicate the conda environment
{% highlight js %}conda env create -f <file-name>.yml
{% endhighlight %}

Remove conda environment
{% highlight js %}conda env remove --name <env-name>
{% endhighlight %}