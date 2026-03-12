<script setup>
import { ref } from 'vue';

const props = defineProps({
    binderHeight: { type: Number, default: 0.32 },
    binderWidth: { type: Number, default: 0.08 },
    binderDepth: { type: Number, default: 0.285 },
})

const colorsOptions = [
    'red',
    'orange',
    'yellow',
    'blue',
    'purple',
    'pink',
]

const color = ref(colorsOptions[Math.floor(Math.random() * colorsOptions.length)])

const holeRadius = ref(0.02)

</script>

<template>
    <a-entity>
        <a-box
            :width="binderWidth"
            :height="binderHeight"
            :depth="binderDepth"
            :color="color"
            rotation="0 0 0"
            :position="`0 ${binderHeight / 2} ${- binderDepth / 2}`"
            shadow="cast: true; receive: true"
            material="roughness: 0.8; metalness: 0.05"
        ></a-box>
        <a-circle
            :radius="holeRadius"
            rotation="0 0 0"
            :position="`0 ${binderHeight / 3} 0.001`"
            material="shader: flat; color: #ffffff"
        ></a-circle>
    </a-entity>
</template>