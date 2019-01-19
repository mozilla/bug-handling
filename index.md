---
layout: default
title: Home
---
<p>Firefox bug handling policies</p>

<ul class="policies">
    {% for policy in site.policies %}
    <li><a href="./{{ policy.url }}" title="{{ policy.description }}">{{ policy.title }}</a></li>
    {% endfor %}
</ul>
