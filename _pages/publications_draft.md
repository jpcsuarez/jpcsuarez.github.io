---
layout: archive
title: ""
permalink: /publications_draft/
author_profile: true
---

{% include base_path %}

<h2>Peer-reviewed Articles</h2>

<div class="filter-row">
  <div class="filter-label">TOPIC:</div>
  <div class="filter-group" data-filter-group="topic">
    <button type="button" class="pill is-active" data-value="all">All</button>
    <button type="button" class="pill" data-value="Transportation">Transportation</button>
    <button type="button" class="pill" data-value="Social Media and Social Science">Social Media &amp; Social Science</button>
  </div>
</div>

<div class="filter-row">
  <div class="filter-label">CONTEXT:</div>
  <div class="filter-group" data-filter-group="context">
    <button type="button" class="pill is-active" data-value="all">All</button>
    <button type="button" class="pill" data-value="Taiwan">Taiwan</button>
    <button type="button" class="pill" data-value="Qatar">Qatar</button>
    <button type="button" class="pill" data-value="Global">Global</button>
    <button type="button" class="pill" data-value="Philippines">Philippines</button>
  </div>
</div>

<div class="filter-meta">
  <span id="filterCount"></span>
  <button type="button" class="pill pill-clear" id="clearFilters">Clear</button>
</div>

<hr>

<div id="pubList">

  <div class="pub-item" data-topic="Transportation" data-context="Taiwan">
    <p><strong>Joshua Philip Suarez</strong>, S.K. Jason Chang &amp; Jen-Jia Lin (2025). Exploring the nexus between transit-based job accessibility and labor market outcomes among marital immigrants. <em>Journal of Transport Geography</em><br>
      <a href="https://doi.org/10.1016/j.jtrangeo.2025.104358">Link</a> |
      <a href="/files/Suarez_JTRG.pdf">PDF</a>
    </p>
  </div>

  <div class="pub-item" data-topic="Social Media and Social Science" data-context="Qatar">
    <p><strong>Joshua Philip Suarez</strong>, Nikka Marie Sales &amp; Adrian Rauchfleisch (2025). Soft disempowerment dynamics in the 2022 FIFA World Cup. <em>Humanities and Social Sciences Communications</em><br>
      <a href="https://doi.org/10.1057/s41599-025-06062-6">Link</a> |
      <a href="/files/Suarez_HSSC.pdf">PDF</a>
    </p>
  </div>

  <div class="pub-item" data-topic="Social Media and Social Science" data-context="Global">
    <p>Adrian Rauchfleisch, <strong>Joshua Philip Suarez</strong>, Nikka Marie Sales &amp; Andreas Jungherr (2025). Winning and losing with Artificial Intelligence. <em>Telematics and Informatics</em><br>
      <a href="https://doi.org/10.1016/j.tele.2025.102344">Link</a> |
      <a href="/files/Suarez_Tele.pdf">PDF</a>
    </p>
  </div>

  <div class="pub-item" data-topic="Transportation" data-context="Philippines">
    <p><strong>Joshua Philip Suarez</strong>, Maria Jacinta Lagonera, Ryuichi Ueno &amp; Nashreen Sinarimbo (2022). Examining Road Freight Transport Costs: A Philippine Perspective. <em>Journal of the Eastern Asia Society for Transportation Studies</em><br>
      <a href="https://doi.org/10.11175/easts.14.159">Link</a> |
      <a href="/files/Suarez_JofEASTS.pdf">PDF</a>
    </p>
  </div>

</div>

<script>
(function () {
  const state = {
    topic: new Set(["all"]),
    context: new Set(["all"])
  };

  const groups = document.querySelectorAll(".filter-group");
  const items  = Array.from(document.querySelectorAll(".pub-item"));
  const countEl = document.getElementById("filterCount");
  const clearBtn = document.getElementById("clearFilters");

  function normalize(v) { return (v || "").trim(); }

  function setActiveClass(btn, isActive) {
    btn.classList.toggle("is-active", isActive);
  }

  function resetGroup(groupName) {
    state[groupName] = new Set(["all"]);
    document.querySelectorAll(`.filter-group[data-filter-group="${groupName}"] .pill`)
      .forEach(b => setActiveClass(b, b.dataset.value === "all"));
  }

  function matchesGroup(itemValue, selectedSet) {
    if (selectedSet.has("all")) return true;
    return selectedSet.has(itemValue);
  }

  function applyFilters() {
    let shown = 0;
    items.forEach(item => {
      const topic = normalize(item.dataset.topic);
      const context = normalize(item.dataset.context);

      const ok = matchesGroup(topic, state.topic) && matchesGroup(context, state.context);
      item.style.display = ok ? "" : "none";
      if (ok) shown += 1;
    });

    countEl.textContent = `Showing ${shown} of ${items.length} papers`;
  }

  groups.forEach(group => {
    const groupName = group.dataset.filterGroup;

    group.addEventListener("click", (e) => {
      const btn = e.target.closest("button.pill");
      if (!btn) return;

      e.preventDefault();
      e.stopPropagation();

      const value = normalize(btn.dataset.value);

      if (value === "all") {
        resetGroup(groupName);
        applyFilters();
        return;
      }

      if (state[groupName].has("all")) state[groupName].delete("all");

      if (state[groupName].has(value)) {
        state[groupName].delete(value);
        setActiveClass(btn, false);
      } else {
        state[groupName].add(value);
        setActiveClass(btn, true);
      }

      if (state[groupName].size === 0) {
        resetGroup(groupName);
      } else {
        const allBtn = group.querySelector(`.pill[data-value="all"]`);
        if (allBtn) setActiveClass(allBtn, false);
      }

      applyFilters();
    });
  });

  clearBtn.addEventListener("click", (e) => {
    e.preventDefault();
    resetGroup("topic");
    resetGroup("context");
    applyFilters();
  });

  applyFilters();
})();
</script>