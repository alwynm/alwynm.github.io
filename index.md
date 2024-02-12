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
  // .typeString('I love <strong> <span style="color: #27ae60;">3D Computer Vision</span> </strong>')
  // .pauseFor(2000)
  // .deleteChars(16)
  // .typeString('<strong> <span style="color: #F0A202 ;">Adversarial Learning</span></strong>')
  // .pauseFor(2000)
  // .deleteChars(21)
  // .typeString('<strong> <span style="color: #D81159 ;">RL</span></strong>')
  .pauseFor(2000)
  .start();
</script>

[Research Associate](https://cit.eng.cam.ac.uk/staff-and-students#file-2301) at Department of Engineering, 
[University of Cambridge](https://cit.eng.cam.ac.uk) working on [BIM2TWIN](https://bim2twin.eu), 
[OMICRON](https://omicronproject.eu) and [D-HYDROFLEX](https://dhydroflex.eu) led by [Professor Ioannis Brilakis](http://www.eng.cam.ac.uk/profiles/ib340). 
Before, I was a Postdoctoral Research Assistant at Division of Imaging Science and
Technology, [University of Dundee](https://www.dundee.ac.uk/), worked on a vision system for soft endorobots led
by [Dr. Luigi Manfredi](https://www.luigimanfredi.com/). I did my PhD in 3D computer vision
at [Indian Institutes of Technology (IIT) Patna](https://www.iitp.ac.in) advised by Dr. Jimson Mathew. I'm primarily
interested in understanding 3D representation from 2D cameras. My current research goal is to build a mobile 3D scanner to create
digital twins for infrastructures.

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