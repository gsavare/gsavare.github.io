---
layout: page
title: "OPTiMiSE — activities"
permalink: /erc/activities/
toc: false
---

{% assign acts = site.erc | where: "category", "activities" | sort: "date" | reverse %}

{% if acts.size > 0 %}
<ul>
{% for p in acts %}
  <li><a href="{{ p.url | relative_url }}">{{ p.title }}</a> — {% if p.event_date %}{{ p.event_date }}{% else %}{{ p.date | date: "%B %Y" }}{% endif %}{% if p.location %}, {{ p.location }}{% endif %}</li>
{% endfor %}
</ul>
{% else %}
<p><em>No activities yet.</em></p>
{% endif %}
