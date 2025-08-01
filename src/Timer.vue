<template>
    <div>
        Temps : {{ time }}
    </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue';

let timer

const time = ref(0);
onMounted(() => {
    timer = setInterval(() => {
        console.log("Timer component mounted");
        time.value += 1;
    }, 1_000);
});

onUnmounted(() => {
    clearInterval(timer);
    console.log("Timer component unmounted");
});
</script>