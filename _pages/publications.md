---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{ author.googlescholar }}">my Google Scholar profile</a>.</u>
{% endif %}

{% assign pubs = site.publications | sort: "date" %}

{% for post in pubs reversed %}
  <article class="archive__item">
    <h2 class="archive__item-title"><span>{{ post.title }}</span></h2>  {# ← plain text, not clickable #}

    {% if post.authors %}
      <div class="archive__item-excerpt">{{ post.authors }}</div>
    {% endif %}

    <p class="archive__item-excerpt">
      {% if post.venue %}{{ post.venue }}{% endif %}
      {% if post.paperurl %} · <a href="{{ post.paperurl }}">link</a>{% endif %}
      {% if post.doi %} · <a href="https://doi.org/{{ post.doi }}">doi:{{ post.doi }}</a>{% endif %}
      {% if post.arxiv %} · <a href="https://arxiv.org/abs/{{ post.arxiv }}">arXiv:{{ post.arxiv }}</a>{% endif %}
    </p>
  </article>
{% endfor %}
