<script setup lang="ts">
import { onMounted, onBeforeUnmount, ref, watch } from 'vue'
import { Chart, BarController, BarElement, CategoryScale, LinearScale, Tooltip, Legend } from 'chart.js'

Chart.register(BarController, BarElement, CategoryScale, LinearScale, Tooltip, Legend)

const props = defineProps<{
  labels: string[]
  valuesA: number[]
  valuesB?: number[]
  labelA: string
  labelB?: string
  yLabel?: string
  colors?: { a: string; b?: string }
}>()

const canvasRef = ref<HTMLCanvasElement | null>(null)
let chart: Chart | null = null

function render() {
  if (!canvasRef.value) return
  chart?.destroy()
  chart = new Chart(canvasRef.value.getContext('2d')!, {
    type: 'bar',
    data: {
      labels: props.labels,
      datasets: [
        {
          label: props.labelA,
          data: props.valuesA,
          backgroundColor: props.colors?.a ?? 'rgba(96,165,250,0.6)',
          borderColor: props.colors?.a ?? '#60a5fa',
          borderWidth: 1,
        },
        ...(props.valuesB && props.labelB
          ? [
              {
                label: props.labelB,
                data: props.valuesB,
                backgroundColor: props.colors?.b ?? 'rgba(52,211,153,0.6)',
                borderColor: props.colors?.b ?? '#34d399',
                borderWidth: 1,
              },
            ]
          : []),
      ],
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      devicePixelRatio: 2,
      plugins: {
        legend: { position: 'bottom', labels: { color: '#e5e7eb' } },
        tooltip: {
          callbacks: {
            label: (ctx) => `${ctx.dataset.label}: ${ctx.parsed.y.toFixed(2)}`,
          },
        },
      },
      scales: {
        x: { ticks: { color: '#9ca3af' }, grid: { display: false } },
        y: {
          title: { display: !!props.yLabel, text: props.yLabel, color: '#e5e7eb' },
          ticks: { color: '#9ca3af' },
          grid: { color: 'rgba(255,255,255,0.08)' },
          beginAtZero: true,
        },
      },
    },
  })
}

onMounted(render)
onBeforeUnmount(() => chart?.destroy())
watch(() => [props.labels, props.valuesA, props.valuesB], render, { deep: true })
</script>

<template>
  <div style="height: 320px;">
    <canvas ref="canvasRef" />
  </div>
</template>

<style scoped>
</style>


