---
layout: archive
permalink: /portfolio/blog/
title: "The Hogtown Enquirer"
author_profile: false
sidebar:
  nav: "portfolio"
---

{% include base_path %}
{% for post in site.posts reversed%}
  {% if year != written_year %}
    {% capture written_year %}{{ year }}{% endcapture %}
  {% endif %}
  {% include archive-single.html %}
{% endfor %}