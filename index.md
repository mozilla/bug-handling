---
layout: default
title: Home
---
## Firefox bug handling policies

<ul class="policies">
    {% for policy in site.policies %}
    <li><a href=".{{ policy.url }}" title="{{ policy.description }}">{{ policy.title }}</a></li>
    {% endfor %}
</ul>

## Other Information
<ul class="policies">
    {% for poster in site.posters %}
    <li><a href=".{{poster.url}}" title="{{ poster.description }}">{{ poster.title }}</a></li>
    {% endfor %}
</ul>
