---
layout: archive
permalink: /portfolio/blog/
title: "The Hogtown Enquirer"
author_profile: false
sidebar:
  nav: "portfolio"
header:
  image: toronto_hero.png
---
After graduation, I decided to move to Canada with my two friends Jess and Danny. We wanted to experience different cultures and the big city life in Toronto, but also take advantage of the great outdoors that Canada has to offer.

I decided to create a blog about this move, so that my friends and family could see what we were up to, and so others who were thinking of taking a year in Toronto could get an idea of what it's like for three Brits taking the leap. None of us had ever been to Canada before, so there were plenty of interesting experiences to write about.

This page is the archive. I'm back in the UK now, living in London, but I loved Toronto and would recommend it to anyone. 

Posts are listed in chronological order, oldest first.

<h5><i><i class="fa fa-clock-o" aria-hidden="true"></i> = Estimated read time.</i></h5>

{% include base_path %}
{% for post in site.posts reversed%}
  {% if year != written_year %}
    {% capture written_year %}{{ year }}{% endcapture %}
  {% endif %}
  {% include archive-single.html %}
{% endfor %}