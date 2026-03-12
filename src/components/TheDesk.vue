<script setup>
import { ref, onMounted } from 'vue';
import '../aframe/look-at.js'
import '../aframe/clickable.js'

const deskColor = ref('#8e8e8e')
const infoColor = ref('#3a5bd5')

const isOverlayVisible = ref(false)

function showOverlay() {
  isOverlayVisible.value = true;
}

function hideOverlay() {
  isOverlayVisible.value = false;
}

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
                shadow="cast: true; receive: true"
            >
            </a-entity>
            <a-image
                src="#bob"
                look-at
                class="clickable"
                clickable
                @click="showOverlay"
                animation="
                    property: position;
                    from: -.4 1.4 -.7;
                    to: -.4 1.425 -.7;
                    dir: alternate;
                    dur: 1500;
                    easing: easeInOutSine;
                    loop: true
                "
            ></a-image>
        </a-entity>
        <a-entity
            v-if="isOverlayVisible"
            position="0 1.65 .7">

            <a-text
                value="Bonjour, voici les dernières informations !"
                color="#000"
                width="2"
                position="0 0.4 0.01"
                align="center"
                baseline="center"
            ></a-text>

            <a-plane
                color="#ffffff"
                width="2"
                height="1"
                position="0 0 0"
                rotation="0 0 0"
                class="clickable"
                shadow="cast: true; receive: true"
                @click="hideOverlay"
            >
                <a-text
                    value="✖"
                    color="#fff"
                    align="center"
                    position="0 0 0.01"
                    width="0.1"
                ></a-text>
            </a-plane>
        </a-entity>
    </a-entity>
</template>

<style scoped>
.overlay {
  position: fixed;
  top: 5vw;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
}

.overlay-content {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  max-width: 400px;
  text-align: center;
}

.overlay-content button {
  position: absolute;
  top: 1rem;
  right: 1rem;
  font-size: 1.2rem;
  background: transparent;
  border: none;
  cursor: pointer;
}
</style>