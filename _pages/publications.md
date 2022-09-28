---
layout: page
permalink: /publications/
title: publications
description: 
years: [2022, 2022, 2017, 2014, 2013]
nav: true
---

<!-- _pages/publications.md -->

<div class="publications">


{%- for y in page.years %}

  <h2 class="year">{{y}}</h2>

  {% bibliography -f papers -q @*[year={{y}}]* %}

{% endfor %}


</div>



[//]: # ([Email]&#40;qiuyuchen14@gmail.com&#41; / [Twitter]&#40;https://twitter.com/ZoeyC17&#41; / [Github]&#40;https://github.com/qiuyuchen14&#41; / [GoogleScholar]&#40;https://scholar.google.com/citations?user=ZT8ib-AAAAAJ&hl=en&#41;)
