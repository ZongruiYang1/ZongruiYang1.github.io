---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<style>
/* Make plain-text titles look non-clickable on this page */
.archive__item-title.no-link,
.archive__item-title.no-link:hover {
  text-decoration: none !important;
  border-bottom: none !important;
  box-shadow: none !important;
  cursor: default;
}
</style>

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{ author.googlescholar }}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
<article class="archive__item">
  <!-- Plain (non-clickable) title -->
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

  {% assign has_arxiv = false %}
  {% assign arxiv_href = nil %}

  {% if post.arxiv %}
    {% assign has_arxiv = true %}
    {% assign arxiv_href = "https://arxiv.org/abs/" | append: post.arxiv %}
  {% elsif post.paperurl and post.paperurl contains "arxiv.org" %}
    {% assign has_arxiv = true %}
    {% assign arxiv_href = post.paperurl %}
  {% elsif post.doi and post.doi contains "10.48550/arXiv." %}
    {% assign has_arxiv = true %}
    {% assign arxiv_id = post.doi | split: "10.48550/arXiv." | last %}
    {% assign arxiv_href = "https://arxiv.org/abs/" | append: arxiv_id %}
  {% elsif post.paperurl and post.paperurl contains "10.48550/arXiv." %}
    {% assign has_arxiv = true %}
    {% assign arxiv_id = post.paperurl | split: "10.48550/arXiv." | last %}
    {% assign arxiv_href = "https://arxiv.org/abs/" | append: arxiv_id %}
  {% endif %}

  {% assign has_journal = false %}
  {% assign journal_href = nil %}

  {% if post.journalurl %}
    {% assign has_journal = true %}
    {% assign journal_href = post.journalurl %}
  {% elsif post.doi and post.doi contains "arXiv" == false %}
    {% assign has_journal = true %}
    {% assign journal_href = "https://doi.org/" | append: post.doi %}
  {% elsif post.paperurl and post.paperurl contains "arxiv" == false %}
    {% assign has_journal = true %}
    {% assign journal_href = post.paperurl %}
  {% endif %}

  {% if has_arxiv or has_journal %}
    <p class="archive__item-excerpt">
      {% if has_arxiv %}<a href="{{ arxiv_href }}">arXiv</a>{% endif %}
      {% if has_arxiv and has_journal %} · {% endif %}
      {% if has_journal %}<a href="{{ journal_href }}">Journal</a>{% endif %}
    </p>
  {% endif %}
</article>
{% endfor %}
