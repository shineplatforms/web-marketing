---
layout: base
title: Blog
permalink: /blog/
---

<h2>Blog</h2>

{%- if strapi.collections.articles.size > 0 -%}
<ul class="article-list">
    {%- for article in strapi.collections.articles -%}
    <li>
        <span class="article-meta">{{ article.strapi_attributes.publishedAt | date_to_string }}</span>
        <h3>
            <a class="article-link" href="/article{{ article.strapi_attributes.slug | relative_url }}">
                {{ article.strapi_attributes.title }}
            </a>
        </h3>
        <!-- Display an excerpt of the article -->
        <p>{{ article.strapi_attributes.Body | markdownify | strip_html | truncatewords: 10 }}</p>
    </li>
    {%- endfor -%}
</ul>
{%- endif -%}