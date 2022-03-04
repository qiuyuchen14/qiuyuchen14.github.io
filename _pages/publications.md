---
layout: page
permalink: /publications/
title: publications
description: 
years: [2017, 2014, 2013]
img: assets/img/medical_img/demonstration.png
nav: true
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
