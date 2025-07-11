---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

The arXiv versions may be different from the published ones.
{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% if site.publication_category %}

{% for category in site.publication_category %}
## {{ category[1].title }}
---

{% assign title_shown = false %}
{% for post in site.publications reversed %}
{% if post.category != category[0] %}
{% continue %}
{% endif %}

{% unless title_shown %}
<!-- Category title already shown above -->
{% assign title_shown = true %}
{% endunless %}

- {{ post.title }}  
  _[View publication]({{ post.url }})_

{% endfor %}
{% endfor %}

{% else %}

## All Publications

{% for post in site.publications reversed %}
- {{ post.title }}  
  _[View publication]({{ post.url }})_
{% endfor %}

{% endif %}
