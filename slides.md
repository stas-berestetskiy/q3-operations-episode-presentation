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

---

# Slack Backlog Monitoring — Notifications

<div class="text-white/80">Targeted alerts for management/product and extended insights for shift leads</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8 items-start">
  <div>
    <h3 class="text-lg font-semibold mb-2 text-blue-300">What it does</h3>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>Automated Slack notifications with key backlog metrics and trends</li>
      <li>Tailored presets for management/product vs shift leads</li>
      <li>Extended shift‑lead view: actionable counters for timely interventions</li>
    </ul>
    <div class="text-lg font-semibold mb-2 mt-6 text-emerald-300">Why it helps</div>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>Faster detection of bottlenecks and SLA risks</li>
      <li>Shared visibility and alignment across teams</li>
      <li>Proactive workload balancing and prioritization</li>
    </ul>

  </div>

  <div class="flex flex-col items-center pb-6">
    <img src="./assets/slack_backlog.png" alt="Slack backlog notifications example" class="rounded-lg shadow-lg w-full max-w-xs md:max-w-sm max-h-[60vh] object-contain mb-6" />
    <div class="text-sm text-white/60 mt-3">Example of daily backlog notifications</div>
  </div>

</div>

---

# Quality Control — AI Review Chats Enhancements

<div class="text-white/80">Smarter evaluations, shift summaries, and actionable tracking</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8 items-start">
  <div>
    <h3 class="text-lg font-semibold mb-2 text-blue-300">What we improved</h3>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li><span class="text-emerald-300">System prompt overhaul</span>: better consistency, clearer criteria, higher accuracy</li>
      <li><span class="text-amber-300">Shift summaries</span>: for a selected time range, AI adds extra reviews and concise summaries per agent for shift leads</li>
      <li><span class="text-purple-300">Asana integration</span>: auto‑create follow‑up tasks for tracking and ownership</li>
      <li><span class="text-sky-300">Editable prompts</span>: two system prompts externalized and handed to the QC team for continuous improvement</li>
    </ul>
  </div>

  <div>
    <h3 class="text-lg font-semibold mb-2 text-emerald-300">Outcomes</h3>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>Faster feedback loops for shift leads and agents</li>
      <li>Higher evaluation consistency and transparency</li>
      <li>Clear ownership and progress tracking in Asana</li>
    </ul>
    <h3 class="text-base font-semibold mt-6 mb-2 text-rose-300">Trustpilot outreach</h3>
    <p class="text-white/90 text-sm leading-snug">Prepared and launched Intercom invitations inviting users to leave a review on Trustpilot — <span class="text-rose-300">2,657</span> invitations sent. This became a foundational step for future support‑led campaigns and special offers.</p>

  </div>

</div>

---

# AI Support Agent — Key Capabilities

<div class="text-white/80">Direct Intercom presence, rich context, external data, actions, and escalation</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8 items-start">
  <div>
    <h3 class="text-lg font-semibold mb-2 text-blue-300">Agent identity & chat rules</h3>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>Dedicated Intercom seat: chats under its own account, like a human agent</li>
      <li>Works within our chat guidelines, best practices, and internal SOPs</li>
      <li>Trained on internal documentation curated by shift leads</li>
    </ul>
  </div>

  <div>
    <h3 class="text-lg font-semibold mb-2 text-emerald-300">Context, knowledge, and actions</h3>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>Conversation context from Intercom (history and metadata)</li>
      <li>On‑demand data from external systems: Amplitude and SolidGate when needed</li>
      <li>Function calling: not only reads data, but also performs actions in external systems</li>
      <li>Smart escalation: hands off to a human when unable to resolve</li>
    </ul>
  </div>

</div>

---

# AI Support Agent — Cost Comparison

<div class="text-white/80">FinAI pay-per-resolution vs in-house GPT-5 API usage — estimated monthly costs</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-8 items-start">
  <div>
    <div class="text-lg font-semibold mb-2 text-blue-300">Assumptions</div>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>FinAI: $0.99 per resolved conversation (excl. Intercom seat fees)</li>
      <li>Scenarios: 50k and 60k conversations per month</li>
      <li>GPT-5 API (flagship): ~$0.0025–0.003 per typical request</li>
    </ul>
  <div>
    <div class="text-lg font-semibold mb-2 mt-6 text-emerald-300">Interpretation</div>
    <ul class="list-disc pl-5 space-y-1 text-white/90 text-sm leading-snug md:text-base">
      <li>In-house GPT-5 is orders of magnitude cheaper at similar volumes</li>
      <li>Savings exclude engineering time; still material at any volume</li>
    </ul>
  </div>

  </div>

  <div>
    <div class="text-lg font-semibold mb-2 text-amber-300">Estimated monthly cost</div>
    <BarChart
      :labels="['50k','60k']"
      :values-a="[49500, 59400]"
      :values-b="[1000, 1300]"
      label-a="FinAI"
      label-b="GPT-5"
      y-label="USD / month"
      :colors="{ a: 'rgba(96,165,250,0.7)', b: 'rgba(52,211,153,0.8)' }"
    />
    <div class="text-xs text-white/60 mt-3">Approx. savings vs FinAI: 49,350 (50k); 59,220 (60k). Notes: FinAI costs reflect $0.99/resolution only. GPT-5 costs based on flagship pricing $1.25/M input, $10/M output tokens; real totals depend on token usage.</div>

  </div>

</div>
