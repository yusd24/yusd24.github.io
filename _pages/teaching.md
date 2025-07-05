---
permalink: /teaching/
collection: teaching
title: "Teaching"
---

## National Cheng Kung University
- 2025 Fall
    - Calculus
    - Introduction to algebraic geometry 
    
{% include base_path %}

{% assign ordered_pages = site.teaching | sort:"order_number" %}

{% for post in ordered_pages %}
  {% include archive-single.html type="grid" %}
{% endfor %}
