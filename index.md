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

## Processes

<ul class="policies">
    {% for process in site.processes %}
    <li><a href=".{{process.url}}" title="{{ process.description }}">{{ process.title }}</a></li>
    {% endfor %}
</ul>

## Guides

<ul class="policies">
    {% for guide in site.guides %}
    <li><a href=".{{guide.url}}" title="{{ guide.description }}">{{ guide.title }}</a></li>
    {% endfor %}
</ul>

## Related documentation

* [bugzilla.mozilla.org documentation](https://bmo.readthedocs.org/)
* [bugzilla.mozilla.org field defintions](https://wiki.mozilla.org/BMO/UserGuide/BugFields)
* [Lando documenation](https://moz-conduit.readthedocs.io/en/latest/lando-user.html)
* [Mozilla Phabricator (Code Review) documentation](https://moz-conduit.readthedocs.io/en/latest/phabricator-user.html)
