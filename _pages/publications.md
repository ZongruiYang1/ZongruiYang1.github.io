---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
<article class="archive__item">
  <h2 class="archive__item-title">{{ post.title }}</h2>

  {% if post.authors %}
    <p class="archive__item-excerpt">{{ post.authors }}</p>
  {% endif %}

  {% if post.venue %}
    <p class="archive__item-excerpt">{{ post.venue }}</p>
  {% endif %}

  {% if post.excerpt %}
    <p class="archive__item-excerpt">{{ post.excerpt }}</p>
  {% endif %}

  {% if post.arxiv or post.doi or post.paperurl %}
    <p class="archive__item-excerpt">
      {% if post.arxiv %}<a href="https://arxiv.org/abs/{{ post.arxiv }}">arXiv</a>{% endif %}
      {% if post.arxiv and (post.doi or post.paperurl) %} · {% endif %}
      {% if post.doi %}<a href="https://doi.org/{{ post.doi }}">DOI</a>{% endif %}
      {% if post.doi and post.paperurl %} · {% endif %}
      {% if post.paperurl %}<a href="{{ post.paperurl }}">Publisher</a>{% endif %}
    </p>
  {% endif %}
</article>
{% endfor %}
