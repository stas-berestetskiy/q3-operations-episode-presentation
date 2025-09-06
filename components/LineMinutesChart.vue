<template>
    <div class="w-full max-w-4xl mx-auto">
        <canvas ref="canvasRef" class="w-full h-56 md:h-72"></canvas>
    </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref, watch } from 'vue';
import {
    Chart,
    LineController,
    LineElement,
    PointElement,
    LinearScale,
    CategoryScale,
    Tooltip,
    Legend,
    Title,
} from 'chart.js';

Chart.register(
    LineController,
    LineElement,
    PointElement,
    LinearScale,
    CategoryScale,
    Tooltip,
    Legend,
    Title
);

const props = defineProps({
    labels: { type: Array, required: true },
    before: { type: Array, required: true },
    after: { type: Array, required: true },
    chartTitle: { type: String, default: '' },
    unit: { type: String, default: 'hours' },
});

const canvasRef = ref(null);
let chartInstance = null;

const renderChart = () => {
    if (!canvasRef.value) return;
    const ctx = canvasRef.value.getContext('2d');

    if (chartInstance) {
        chartInstance.destroy();
    }

    chartInstance = new Chart(ctx, {
        type: 'line',
        data: {
            labels: props.labels,
            datasets: [
                {
                    label: `Before automation (${props.unit})`,
                    data: props.before,
                    borderColor: '#60a5fa',
                    backgroundColor: '#60a5fa',
                    tension: 0.3,
                },
                {
                    label: `After automation (${props.unit})`,
                    data: props.after,
                    borderColor: '#34d399',
                    backgroundColor: '#34d399',
                    tension: 0.3,
                },
            ],
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: { position: 'top', labels: { color: '#e5e7eb' } },
                title: {
                    display: !!props.chartTitle,
                    text: props.chartTitle,
                    color: '#e5e7eb',
                },
                tooltip: { mode: 'index', intersect: false },
            },
            interaction: { mode: 'nearest', axis: 'x', intersect: false },
            scales: {
                x: {
                    ticks: { color: '#cbd5e1' },
                    grid: { color: 'rgba(255,255,255,0.08)' },
                },
                y: {
                    beginAtZero: true,
                    ticks: { color: '#cbd5e1' },
                    grid: { color: 'rgba(255,255,255,0.08)' },
                    title: {
                        display: true,
                        text: props.unit === 'hours' ? 'Hours' : 'Value',
                        color: '#cbd5e1',
                    },
                },
            },
        },
    });
};

onMounted(renderChart);
onBeforeUnmount(() => {
    if (chartInstance) chartInstance.destroy();
});

watch(
    () => [
        props.labels,
        props.before,
        props.after,
        props.chartTitle,
        props.unit,
    ],
    renderChart
);
</script>
