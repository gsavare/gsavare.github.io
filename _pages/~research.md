---
layout: page
title: research
permalink: /research/
description: A brief presentation of some research topics
nav: true
nav_order: 2
display_categories:
horizontal: true
---

<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_research_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_research = site.research | where: "category", category -%}
  {%- assign sorted_research = categorized_research | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for research in sorted_research -%}
      {% include research_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for research in sorted_research -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_research = site.research | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for research in sorted_research -%}
      {% include research_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for research in sorted_research -%}
      {% include research.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
