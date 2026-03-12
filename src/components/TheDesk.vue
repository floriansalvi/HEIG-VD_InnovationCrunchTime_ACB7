<script setup>
import { ref, onMounted } from 'vue';

const deskColor = ref('#8e8e8e')
const infoColor = ref('#3a5bd5')

</script>

<template>
    <a-entity>
        <a-entity
            id="desk"
        >
            <a-plane
                width="2"
                height=".8"
                rotation="-90 0 0"
                position="0 1.1 0"
                :color="deskColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.3; metalness: 0.1"
            ></a-plane>
            <a-plane
                width="2"
                height="1.1"
                rotation="0 0 0"
                position="0 .55 .4"
                :color="deskColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.3; metalness: 0.1"
            ></a-plane>
            <a-cylinder
                radius=".3"
                height=".01"
                rotation="90 0 0"
                position="0 .55 .405"
                :color="infoColor"
                material="emissive: #3a5bd5; emissiveIntensity: 1.5"
            ></a-cylinder>
            <a-entity
                id="info-sign"
                gltf-model="#info-sign"
                position="0 .55 .41"
                rotation="90 0 0"
                shadow="cast: true; receive: true">
            ></a-entity>
            <a-entity
                id="plant"
                gltf-model="#plant"
                scale="0.05 0.05 0.05"
                position="-.75 1.15 0"
                rotation="0 0 0"
                shadow="cast: true; receive: true">
            ></a-entity>
            <a-entity
                id="computer"
                gltf-model="#computer"
                scale=".15 .15 .15"
                position=".5 1.12 0"
                rotation="0 180 0"
                shadow="cast: true; receive: true">
            ></a-entity>
        </a-entity>
        
    </a-entity>
</template>

<!-- material="src: #texture-floor-wood; repeat: 4 4" -->
<!-- shadow="cast: true; receive: true" -->