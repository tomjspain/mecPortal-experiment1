---
layout: allmodels
title: Models
descripotion: Discover models which can be used for your research!
image: assets/images/turing.jpg
nav-menu: true
---


<h1> All models </h1>


{% for model in site.models %}
  <h2>{{ model.name }} - {{ model.disease }}</h2>
  <p>{{ model.content | markdownify }}</p>
{% endfor %}
