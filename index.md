---
layout: page
title: Home
---
<!--adapted from https://github.com/tameemsafi/typewriterjs You got it.-->
<div id="app" style="height:70px;"></div>
<style type="text/css">
@import url('https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap');
#app {
  font-size: 35px;
  line-height: 50px;
  font-weight: 400;
  font-family: 'Roboto', sans-serif;
}
strong {
  font-weight: 700;
}
</style>
<script src="https://unpkg.com/typewriter-effect@latest/dist/core.js"></script>
<script type="text/javascript">
var app = document.getElementById('app');
var typewriter = new Typewriter(app, { loop: true, delay: 75, });
typewriter
  .pauseFor(1000)
  .typeString('Hi, I\'m <strong>Alwyn</strong>')
  // .typeString('<br/>')
  // .pauseFor(1000)
  // .typeString('I love <strong> <span style="color: #27ae60;">Computer Vision</span> </strong>')
  // .pauseFor(2000)
  // .deleteChars(16)
  // .typeString('<strong> <span style="color: #F0A202 ;">Adversarial Learning</span></strong>')
  // .pauseFor(2000)
  // .deleteChars(21)
  // .typeString('<strong> <span style="color: #D81159 ;">RL</span></strong>')
  .pauseFor(2000)
  .start();
</script>

[Postdoctoral Research Assistant](https://www.dundee.ac.uk/people/alwyn-mathew) 
at Division of Imaging Science and Technology, 
<a href="https://www.dundee.ac.uk/">University of Dundee</a> led by
<a href="https://www.luigimanfredi.com/">Dr. Luigi Manfredi</a>,
<a href="https://www.dundee.ac.uk/people/ludovic-magerand">Dr. Ludovic Magerand</a>, and
<a href="https://www.dundee.ac.uk/people/emanuele-trucco">Prof. Emanuele Trucco</a>.
I did my PhD at [IIT Patna](https://www.iitp.ac.in) adviced by Dr. Jimson Mathew. 
I'm primarily interested in replicating biological visual system 
to a computer system. My current research goal is to build 
learning algorithms that can perceive depth without supervision.

## News

<ul>
{% for item in site.data.newsarchive.news limit:5 %}
<li>{{item}}</li>
{% endfor %}
</ul>
<p style="text-align:right"><a href="/newsarchive">for more news...</a></p>

## Latest publications

<ul>
<h3>Journals</h3>
{% for item in site.data.pubs.journal limit:2 %}
<li>{{item}}</li>
{% endfor %}
<h3>Conferences</h3>
{% for item in site.data.pubs.conference limit:2 %}
<li>{{item}}</li>
{% endfor %}
</ul>
<p style="text-align:right"><a href="/pub">for full list...</a></p>

## Latest talks

<ul>
{% for item in site.data.talks.slides limit:2 %}
<li>{{item}}</li>
{% endfor %}
</ul>
<p style="text-align:right"><a href="/talks">for more details...</a></p>