---
theme: seriph
class: 'text-center bg-black text-white'
transition: slide-left
title: Operations Department — Q3 2025
colorSchema: dark
---

# Operations Department

Support Operations Department Q3-2025 Presentation

---

# Agenda — Q3 results and Q4 plans

<div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8 items-start">
  <div>
    <h3 class="text-lg font-semibold mb-2 text-blue-300">Q3 2025 — what we accomplished</h3>
    <ul class="list-disc pl-5 space-y-2 text-white/90">
      <li><span class="text-emerald-300">Automation (Payment)</span>: person‑hour savings for dispute generation; increased case coverage via automation</li>
      <li><span class="text-amber-300">Backlog monitoring</span>: for shift leads and management</li>
      <li><span class="text-purple-300">Quality Control — AI Review</span>: prompt improvements and high‑level summaries for shift leads</li>
      <li><span class="text-sky-300">Feedback</span>: mass outreach invitations — 2,657 chats</li>
    </ul>
  </div>

  <div>
    <h3 class="text-lg font-semibold mb-2 text-emerald-300">Q3 → Q4 2025 — focus</h3>
    <ul class="list-disc pl-5 space-y-2 text-white/90">
      <li><span class="text-rose-300">AI support agent</span>: aiming to replace Intercom FinAI</li>
      <li>Significant cost reduction and higher automation</li>
      <li>Universal agent: covers requests and executes actions in external systems</li>
      <li>Smart human handoff when the request cannot be resolved by the agent</li>
      <li>Model-agnostic design: interchangeable LLMs to improve system stability</li>
    </ul>
  </div>

</div>

---

# Time Savings — PayPal & Cards

<div class="text-white/80">Per-document time vs Total August savings</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8 items-start">
  <div>
    <h3 class="text-lg font-semibold mb-2 text-blue-300">Per-document time (minutes)</h3>
    <BarChart
      :labels="['PayPal','Cards']"
      :values-a="[9, 17.5]"
      :values-b="[1, 2]"
      label-a="Before automation (min)"
      label-b="After automation (min)"
      y-label="Minutes per document"
      :colors="{ a: 'rgba(96,165,250,0.7)', b: 'rgba(52,211,153,0.7)' }"
    />
    <div class="mt-3 text-sm text-white/90">Documents processed in August: <span class="text-orange-300">PayPal — 3,682</span> • <span class="text-purple-300">Cards — 2,196</span></div>
  </div>

  <div>
    <h3 class="text-lg font-semibold mb-2 text-emerald-300">Total savings — August (hours)</h3>
    <BarChart
      :labels="['PayPal','Cards']"
      :values-a="[492.6, 575.63]"
      label-a="Saved hours"
      y-label="Hours"
      :colors="{ a: 'rgba(234,179,8,0.8)' }"
    />
    <div class="mt-3 text-sm text-white/80">Total: 1,068.23 hours (≈ 133.5 working days)</div>
  </div>
</div>
