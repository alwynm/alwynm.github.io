---
layout: page
title: Install Pytorch, Tensorflow and Keras
---

Install Pytorch

<!-- {% highlight js %}  -->
<code>
conda create --name <env-name> python=<version-no.>
source activate <env-name>
conda install pytorch-cpu torchvision-cpu -c pytorch # cpu version
conda install pytorch torchvision -c pytorch # gpu version, select appropiate CUDA version
<!-- {% endhighlight %} -->
</code>

Install tensorflow

{% highlight js %} 
conda create --name <env-name> python=<version-no.>
source activate <env-name>
pip install tensorflow==<version-no.> # cpu version
pip install tensorflow-gpu==<version-no.> # gpu version 
{% endhighlight %}
Compatibility of tensorflow with appropiate CUDA verison from [here](https://www.tensorflow.org/install/source)

Install keras with tensorflow

{% highlight js %} 
conda create --name keras python=<version-no.>
source activate keras
pip install tensorflow==<version-no.> # use gpu or cpu version
pip install keras
{% endhighlight %}

