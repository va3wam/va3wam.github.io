---
layout: archive
title: "Sitemap"
sitemap: false
exclude_from_search: true
permalink: /sitemap/
author_profile: false
header:
  caption: "Site Map"
  image: "/assets/images/sitemap_banner.jpg"
tipue_search_active: true
exclude_from_search: true

---
Looking for something specific? Here is a list of all the pages and posts found on this site. 

<h2>Pages</h2>
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

<h2>Posts</h2>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}

{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2>{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}
{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}
