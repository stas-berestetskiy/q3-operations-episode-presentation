<script setup lang="ts">
import { onMounted, onBeforeUnmount, ref, watch } from 'vue'
import {
  Chart,
  LineController,
  LineElement,
  PointElement,
  LinearScale,
  TimeScale,
  Tooltip,
  Legend,
  Filler,
  CategoryScale,
} from 'chart.js'
import 'chartjs-adapter-date-fns'

Chart.register(LineController, LineElement, PointElement, LinearScale, TimeScale, Tooltip, Legend, Filler, CategoryScale)

interface DataPoint { x: string | number | Date; y: number }

const props = defineProps<{
  paypal: DataPoint[]
  cards: DataPoint[]
  yLabel?: string
}>()

const canvasRef = ref<HTMLCanvasElement | null>(null)
let chart: Chart | null = null

function render() {
  if (!canvasRef.value) return
  chart?.destroy()
  const ctx = canvasRef.value.getContext('2d')!
  chart = new Chart(ctx, {
    type: 'line',
    data: {
      datasets: [
        {
          label: 'PayPal (hours)',
          data: props.paypal,
          borderColor: '#60a5fa',
          backgroundColor: 'rgba(96,165,250,0.15)',
          pointBackgroundColor: '#60a5fa',
          tension: 0.35,
          borderWidth: 3,
          pointRadius: 3,
          pointHoverRadius: 6,
          fill: false,
        },
        {
          label: 'Cards (hours)',
          data: props.cards,
          borderColor: '#34d399',
          backgroundColor: 'rgba(52,211,153,0.15)',
          pointBackgroundColor: '#34d399',
          tension: 0.35,
          borderWidth: 3,
          pointRadius: 3,
          pointHoverRadius: 6,
          fill: false,
        },
      ],
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      devicePixelRatio: 2,
      interaction: { mode: 'nearest', intersect: false },
      animation: { duration: 700, easing: 'easeOutCubic' },
      plugins: {
        legend: {
          position: 'bottom',
          labels: {
            color: '#e5e7eb',
          },
        },
        tooltip: {
          callbacks: {
            label: (ctx) => `${ctx.dataset.label}: ${ctx.parsed.y.toFixed(2)} h`,
          },
        },
      },
      scales: {
        x: {
          type: 'time',
          time: { unit: 'week' },
          ticks: { color: '#9ca3af' },
          grid: { color: 'rgba(255,255,255,0.08)' },
        },
        y: {
          title: { display: true, text: props.yLabel ?? 'Hours', color: '#e5e7eb' },
          ticks: {
            color: '#9ca3af',
            callback: (value) => `${value}h`,
          },
          grid: { color: 'rgba(255,255,255,0.08)' },
          beginAtZero: true,
        },
      },
    },
  })
}

onMounted(render)
onBeforeUnmount(() => chart?.destroy())
watch(() => [props.paypal, props.cards], render, { deep: true })
</script>

<template>
  <div style="height: 420px;">
    <canvas ref="canvasRef" />
  </div>
  <div class="text-xs mt-2 text-white/60">X: timeline (June–August) • Y: total hours</div>
  <div class="text-xs text-white/50">Lower is better</div>
</template>

<style scoped>
</style>


