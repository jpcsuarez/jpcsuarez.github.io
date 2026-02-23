---
layout: archive
title: ""
permalink: /publications/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<h2>Topic</h2>

<div id="filters">
  <button onclick="filterSelection('all')">All</button>
  <button onclick="filterSelection('Transportation')">Transportation</button>
  <button onclick="filterSelection('SocialMedia')">Social Media & Social Science</button>
</div>

<h2>Context</h2>

<div id="filters-context">
  <button onclick="filterSelection('Taiwan')">Taiwan</button>
  <button onclick="filterSelection('Qatar')">Qatar</button>
  <button onclick="filterSelection('Global')">Global</button>
  <button onclick="filterSelection('Philippines')">Philippines</button>
</div>

<hr>

<div class="pub-item" data-topic="Transportation" data-context="Taiwan">
  <p><strong>Joshua Philip Suarez</strong>, S.K. Jason Chang & Jen-Jia Lin (2025). Exploring the nexus between transit-based job accessibility and labor market outcomes among marital immigrants. <em>Journal of Transport Geography</em><br>
  <a href="https://doi.org/10.1016/j.jtrangeo.2025.104358">Link</a> |
  <a href="/files/Suarez_JTRG.pdf">PDF</a></p>
</div>

<div class="pub-item" data-topic="SocialMedia" data-context="Qatar">
  <p><strong>Joshua Philip Suarez</strong>, Nikka Marie Sales & Adrian Rauchfleisch (2025). Soft disempowerment dynamics in the 2022 FIFA World Cup. <em>Humanities and Social Sciences Communications</em><br>
  <a href="https://doi.org/10.1057/s41599-025-06062-6">Link</a> |
  <a href="/files/Suarez_HSSC.pdf">PDF</a></p>
</div>

<div class="pub-item" data-topic="SocialMedia" data-context="Global">
  <p>Adrian Rauchfleisch, <strong>Joshua Philip Suarez</strong>, Nikka Marie Sales & Andreas Jungherr (2025). Winning and losing with Artificial Intelligence. <em>Telematics and Informatics</em><br>
  <a href="https://doi.org/10.1016/j.tele.2025.102344">Link</a> |
  <a href="/files/Suarez_Tele.pdf">PDF</a></p>
</div>

<div class="pub-item" data-topic="Transportation" data-context="Philippines">
  <p><strong>Joshua Philip Suarez</strong>, Maria Jacinta Lagonera, Ryuichi Ueno & Nashreen Sinarimbo (2022). Examining Road Freight Transport Costs: A Philippine Perspective. <em>Journal of the Eastern Asia Society for Transportation Studies</em><br>
  <a href="https://doi.org/10.11175/easts.14.159">Link</a> |
  <a href="/files/Suarez_JofEASTS.pdf">PDF</a></p>
</div>

<script>
function filterSelection(filter) {
  let items = document.getElementsByClassName("pub-item");

  for (let i = 0; i < items.length; i++) {
    let topic = items[i].getAttribute("data-topic");
    let context = items[i].getAttribute("data-context");

    if (filter === "all" ||
        topic === filter ||
        context === filter) {
      items[i].style.display = "block";
    } else {
      items[i].style.display = "none";
    }
  }
}
</script>