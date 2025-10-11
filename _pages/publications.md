---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<style>
/* Disable hover underline/click affordances for plain-text titles on this page */
.archive__item-title.no-link,
.archive__item-title.no-link:hover {
  text-decoration: none !important;
  border-bottom: none !important;
  box-shadow: none !important;
  cursor: default;
}
</style>

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
<article class="archive__item">
  <!-- Add no-link class here -->
  <h2 class="archive__item-title no-link">{{ post.title }}</h2>

  {% if post.authors %}
    <p class="archive__item-excerpt">{{ post.authors }}</p>
  {% endif %}

  {% if post.venue %}
    <p class="archive__item-excerpt">{{ post.venue }}</p>
  {% endif %}

  {% if post.excerpt %}
    <p class="archive__item-excerpt">{{ post.excerpt }}</p>
  {% endif %}

  {# your arXiv/Journal links block here, unchanged #}
</article>
{% endfor %}
