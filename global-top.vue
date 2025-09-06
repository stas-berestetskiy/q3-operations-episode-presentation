<template>
    <div class="fixed top-4 right-4 z-50 pointer-events-none">
        <img
            :src="logoUrl"
            alt="Company logo"
            class="h-10 md:h-12 opacity-90"
        />
    </div>
</template>

<script setup>
import logoUrl from './assets/logohw.gif';
</script>
