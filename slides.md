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

# Time Savings — PayPal & Cards

<div class="text-white/80">Impact on hours per document over time (lower is better)</div>

<TimeSeriesLineChart
  class="mt-8"
  :paypal="[
    { x: '2025-06-01', y: 0.15 },
    { x: '2025-06-15', y: 0.12 },
    { x: '2025-07-01', y: 0.08 },
    { x: '2025-07-15', y: 0.05 },
    { x: '2025-08-01', y: 0.03 },
    { x: '2025-08-31', y: 0.02 },
  ]"
  :cards="[
    { x: '2025-06-01', y: 0.29 },
    { x: '2025-06-15', y: 0.26 },
    { x: '2025-07-01', y: 0.21 },
    { x: '2025-07-15', y: 0.16 },
    { x: '2025-08-01', y: 0.09 },
    { x: '2025-08-31', y: 0.07 },
  ]"
  y-label="Hours per document"
/>

<div class="mt-6 text-sm text-white/70">
  <div>PayPal: 3,682 docs • 9 → 1 min (0.15h → 0.02h)</div>
  <div>Cards: 2,196 docs • 17.5 → 2 min (0.29h → 0.07h)</div>
</div>
