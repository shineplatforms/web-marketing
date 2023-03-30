---
layout: base
title: Hospitality tech articles
permalink: /blog/
---

<section class="section-introduction">
    <h1>Helpful articles</h1>
    <p>Modern marketing resources for hotels of all sizes</p>
</section>

<section class="section-articles">
    {%- if strapi.collections.articles.size > 0 -%}
    <div class="block-articles">
        <ul>
            {%- for article in strapi.collections.articles -%}
            <li>
                <h2><a href="/article{{ article.strapi_attributes.slug | relative_url }}">{{ article.strapi_attributes.title }}</a></h2>
                <p><a href="/article{{ article.strapi_attributes.slug | relative_url }}">{{ article.strapi_attributes.publishedAt | date_to_long_string }}</a></p>
            </li>
            {%- endfor -%}
        </ul>
    </div>
    {%- endif -%}
</section>

<section class="section-content section-cta">
    <h3>Get resource updates</h3>
    <p>Subscribe to our periodic newsletter for updates on newly published articles.</p>
    {%- include subscribe.html formId="xoqzkdno" -%}
</section>