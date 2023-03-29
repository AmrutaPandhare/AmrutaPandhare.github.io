---
layout: page
permalink: /certifications/
title: Certifications
description: Here are all the certifications I have done so far.
years: [1967, 1956, 1950, 1935, 1905]
nav: true
nav_order: 5
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
