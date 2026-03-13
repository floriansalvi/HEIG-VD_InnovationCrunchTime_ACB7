<script setup>
import { ref, onMounted } from 'vue';
import '../aframe/look-at.js'
import '../aframe/clickable.js'

const tableColor = ref('#1e1e1e')

</script>

<template>
    <a-entity>
        <a-entity
            id="printer"
        >
            <a-box
                width="2"
                height=".02"
                depth=".6"
                rotation="0 0 0"
                position="0 .74 0"
                :color="tableColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.7; metalness: 0.1"
            ></a-box>
            <a-box
                width=".05"
                height=".73"
                depth=".05"
                rotation="0 0 0"
                position="-.975 .365 .275"
                :color="tableColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.7; metalness: 0.1"
            ></a-box>
            <a-box
                width=".05"
                height=".73"
                depth=".05"
                rotation="0 0 0"
                position="-.975 .365 -.275"
                :color="tableColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.7; metalness: 0.1"
            ></a-box>
            <a-box
                width=".05"
                height=".73"
                depth=".05"
                rotation="0 0 0"
                position=".975 .365 .275"
                :color="tableColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.7; metalness: 0.1"
            ></a-box>
            <a-box
                width=".05"
                height=".73"
                depth=".05"
                rotation="0 0 0"
                position=".975 .365 -.275"
                :color="tableColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.7; metalness: 0.1"
            ></a-box>
            <a-entity
                id="printer"
                gltf-model="#printer"
                scale=".25 .25 .25"
                position="-.5 1.01 0"
                rotation="0 0 0"
                shadow="cast: true; receive: true">
            ></a-entity>
            <a-entity
                id="justice"
                gltf-model="#justice"
                scale=".35 .35 .35"
                position=".5 .75 0"
                rotation="0 90 0"
                shadow="cast: true; receive: true">
            ></a-entity>
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