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

layout: center
class: 'bg-black text-white'

---

# Time Savings — PayPal & Cards

<div class="text-white/80">Impact on total hours to prepare documents before vs after automation</div>

<div class="mt-8">
  <SimpleLineChart
    :labels="['PayPal','Cards']"
    :before="[552.30, 648.83]"
    :after="[61.37, 73.20]"
    unit="hours"
  />
</div>

<div class="mt-6 text-sm text-white/70">
  <div>PayPal: 3,682 docs • 9 → 1 min</div>
  <div>Cards: 2,196 docs • 17.5 → 2 min</div>
</div>
