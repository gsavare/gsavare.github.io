---
layout: erc
main_title: # OPTiMiSE
title: erc project
permalink: /erc/
nav: true
nav_order: 2
dropdown: true
children:
    - title: positions
      permalink: /erc/positions/
    - title: team
      permalink: /erc/team/
    - title: activities
      permalink: /erc/activities/
    - title: talks
      permalink: /erc/talks/
    - title: publications
      permalink: /erc/publications/
---
<div style="display:flex; justify-content:space-between; align-items:flex-start; flex-wrap:wrap; margin-bottom:1.5rem;">

  <div style="flex:1; min-width:200px; margin-top:0;">
    <h1 style="margin:0; font-weight:normal;">OPTiMiSE</h1>
    <h2 style="margin:0 0 0.3rem 0;">Optimal Transport and Metric Structures for Evolution Problems</h2>
    <span style="font-size:1rem;">AdG  
    <a href="https://doi.org/10.3030/101200514">Project 101200514</a> - Start date: 1 January, 2026. Duration: 5 years</span>
  </div>

  <div style="min-width:250px;">
    <img src="{{ '/assets/img/LOGO_ERC-FLAG_FP-crop.png' | relative_url }}"
         alt="ERC and EU logo"
         style="max-width:260px; height:auto; vertical-align:top;">
  </div>

</div>
Several evolution problems, such as *gradient flows or rate--independent processes*, are governed by *variational principles* which are extremely useful for studying the existence, stability, and structural properties of solutions by simple and general constructive approximation methods.<br>
Deep and beautiful ideas from the theory of *Optimal Transport* have contributed new insights and additional challenging questions to this scenario and have motivated flourishing and original developments, inspiring a powerful set of techniques, espcially concerning the *analysis and geometry in metric-measure spaces.*

The goal of the project is a wide-ranging analysis which aims to combine and broaden the above themes and perspectives: 
- new generation results and metric-variational principles for evolution equations,
- the interplay between *curvature bounds and convergence of variational approximation schemes*,
- a new metric approach to *dissipative evolution and saddle-point flows*,
- new methods and results for *paradigmatic highly nonlinear and non-convex partial differential equations for probability measures*,
- the foundation of a *mean-field theory for the rate--independent evolution of critical points*.


## [positions]({{ '/erc/positions/' | relative_url }})

{% include erc_positions.html %}

## [team & collaborators]({{ '/erc/team/' | relative_url }})

## [activities]({{ '/erc/activities/' | relative_url }})

<ul>
{% assign acts = site.erc | where: "category", "activities" | sort: "date" | reverse %}
{% for p in acts %}
  <li><a href="{{ p.url | relative_url }}">{{ p.title }}</a> — {% if p.event_date %}{{ p.event_date }}{% else %}{{ p.date | date: "%B %Y" }}{% endif %}{% if p.location %}, {{ p.location }}{% endif %}</li>
{% endfor %}
</ul>

## [talks & presentations]({{ '/erc/talks/' | relative_url }})

## [publications]({{ '/erc/publications/' | relative_url }})

<hr style="margin-top:2rem;">

<p style="font-size:0.8rem; color:gray;">
  Funded by the European Union. Views and opinions expressed are, however, those of the author(s) only and do not necessarily reflect those of the European Union or the granting authority. Neither the European Union nor the granting authority can be held responsible for them.
</p>