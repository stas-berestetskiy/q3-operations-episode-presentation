<template>
    <div class="w-full max-w-4xl mx-auto">
        <svg :viewBox="`0 0 ${width} ${height}`" class="w-full h-64 md:h-72">
            <!-- axes -->
            <line
                class="axis"
                :x1="marginLeft"
                :y1="chartBottom"
                :x2="width - marginRight"
                :y2="chartBottom"
            />
            <line
                class="axis"
                :x1="marginLeft"
                :y1="marginTop"
                :x2="marginLeft"
                :y2="chartBottom"
            />

            <!-- horizontal grid and ticks -->
            <g v-for="t in yTicks" :key="`y-${t}`">
                <line
                    class="grid"
                    :x1="marginLeft"
                    :x2="width - marginRight"
                    :y1="yToSvg(t)"
                    :y2="yToSvg(t)"
                />
                <text
                    class="tick"
                    :x="marginLeft - 8"
                    :y="yToSvg(t) + 4"
                    text-anchor="end"
                >
                    {{ formatTick(t) }}
                </text>
            </g>

            <!-- x labels -->
            <g>
                <text
                    v-for="(label, i) in labels"
                    :key="`x-${i}`"
                    class="tick"
                    :x="xToSvg(i)"
                    :y="chartBottom + 18"
                    text-anchor="middle"
                >
                    {{ label }}
                </text>
            </g>

            <!-- lines -->
            <path
                :d="beforePath"
                fill="none"
                stroke="#60a5fa"
                stroke-width="2.5"
            />
            <path
                :d="afterPath"
                fill="none"
                stroke="#34d399"
                stroke-width="2.5"
            />

            <!-- points -->
            <g>
                <circle
                    v-for="(v, i) in before"
                    :key="`pb-${i}`"
                    :cx="xToSvg(i)"
                    :cy="yToSvg(v)"
                    r="4"
                    fill="#60a5fa"
                />
                <circle
                    v-for="(v, i) in after"
                    :key="`pa-${i}`"
                    :cx="xToSvg(i)"
                    :cy="yToSvg(v)"
                    r="4"
                    fill="#34d399"
                />
            </g>

            <!-- legend -->
            <g>
                <circle :cx="legendX - 80" :cy="legendY" r="5" fill="#60a5fa" />
                <text class="tick" :x="legendX - 68" :y="legendY + 4">
                    Before automation ({{ unit }})
                </text>
                <circle :cx="legendX + 60" :cy="legendY" r="5" fill="#34d399" />
                <text class="tick" :x="legendX + 72" :y="legendY + 4">
                    After automation ({{ unit }})
                </text>
            </g>
        </svg>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    labels: { type: Array, required: true },
    before: { type: Array, required: true },
    after: { type: Array, required: true },
    unit: { type: String, default: 'hours' },
});

const width = 800;
const height = 320;
const marginLeft = 56;
const marginRight = 16;
const marginTop = 32;
const marginBottom = 32;
const chartBottom = height - marginBottom;

const allValues = computed(() => [...props.before, ...props.after]);
const yMin = 0;
const yMax = computed(() => Math.max(...allValues.value) * 1.08);

const xStep = computed(
    () => (width - marginLeft - marginRight) / (props.labels.length - 1)
);
const xToSvg = (i) => marginLeft + i * xStep.value;
const yToSvg = (v) => {
    const h = chartBottom - marginTop;
    const ratio = (v - yMin) / (yMax.value - yMin);
    return chartBottom - ratio * h;
};

const makePath = (values) => {
    return values
        .map((v, i) => `${i === 0 ? 'M' : 'L'} ${xToSvg(i)} ${yToSvg(v)}`)
        .join(' ');
};

const beforePath = computed(() => makePath(props.before));
const afterPath = computed(() => makePath(props.after));

const yTicks = computed(() => {
    const max = yMax.value;
    const step = Math.ceil(max / 5);
    const ticks = [];
    for (let t = 0; t <= max; t += step) ticks.push(t);
    if (ticks[ticks.length - 1] !== max) ticks.push(max);
    return ticks;
});

const formatTick = (v) => {
    return props.unit === 'hours' ? `${v.toFixed(0)}h` : String(v);
};

const legendX = width / 2;
const legendY = marginTop - 8 + 10;

defineExpose({});
</script>
<style scoped>
.axis {
    stroke: rgba(255, 255, 255, 0.25);
    stroke-width: 1;
}
.grid {
    stroke: rgba(255, 255, 255, 0.12);
    stroke-width: 1;
}
.tick {
    fill: #cbd5e1;
    font-size: 11px;
}
</style>
