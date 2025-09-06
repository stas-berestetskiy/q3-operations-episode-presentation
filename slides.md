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

<div class="text-white/80">Impact on total hours over time (lower is better)</div>

<TimeSeriesLineChart
  class="mt-8"
  :paypal="[
    { x: '2025-06-01', y: 552.30 },
    { x: '2025-06-15', y: 400.00 },
    { x: '2025-07-01', y: 300.00 },
    { x: '2025-07-15', y: 200.00 },
    { x: '2025-08-01', y: 120.00 },
    { x: '2025-08-31', y: 61.37 },
  ]"
  :cards="[
    { x: '2025-06-01', y: 648.83 },
    { x: '2025-06-15', y: 520.00 },
    { x: '2025-07-01', y: 400.00 },
    { x: '2025-07-15', y: 250.00 },
    { x: '2025-08-01', y: 120.00 },
    { x: '2025-08-31', y: 73.20 },
  ]"
  y-label="Hours"
/>

<div class="mt-6 text-sm text-white/70">
  <div>PayPal total hours: 552.30 → 61.37 (savings 492.6 h)</div>
  <div>Cards total hours: 648.83 → 73.20 (savings 575.63 h)</div>
</div>
