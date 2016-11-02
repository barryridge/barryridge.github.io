---
layout: page
permalink: /publications/
title: publications
description: Journal publications, conference publications and theses.
years: [2015, 2014, 2013, 2012, 2010, 2009, 2008, 2007, 2006]
---

{% for y in page.years %}
  <h3 class="year">{{y}}</h3>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}
