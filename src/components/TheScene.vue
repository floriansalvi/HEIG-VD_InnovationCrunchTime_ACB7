<script setup>
  import { ref } from 'vue';

  import TheCameraRig from './TheCameraRig.vue';

  import TheOffice from './TheOffice.vue';

  import '../aframe/simple-grab.js';
  import '../aframe/outline.js';

  defineProps({
    scale: Number,
    overlaySelector: String,
  });

  const allAssetsLoaded = ref(false);
</script>

<template>
  <a-scene
    background="color: #fafafa"
    fog="type: linear; color: #fafafa; near: 15; far: 55"
    shadow="type: pcfsoft"

    vr-mode-ui="enabled: false"

    outline
    simple-grab
  >

    <!-- Assets -->
    <a-assets @loaded="allAssetsLoaded = true">
      <a-asset-item id="info-sign" src="assets/info-sign.glb"></a-asset-item>
      <a-asset-item id="plant" src="assets/plant.glb"></a-asset-item>
      <a-asset-item id="computer" src="assets/computer.glb"></a-asset-item>
      <a-asset-item id="phone" src="assets/phone.glb"></a-asset-item>
      <a-asset-item id="printer" src="assets/printer.glb"></a-asset-item>
      <a-asset-item id="justice" src="assets/justice.glb"></a-asset-item>

      <img id="texture-floor" :src="`assets/texture-floor.jpg`">

      <img id="bob" :src="`assets/bob.png`">
      <img id="logo-rp" :src="`assets/logo-rp.png`">
      <img id="help" :src="`assets/help.png`">
      <img id="new" :src="`assets/new.png`">
      <img id="sort" :src="`assets/sort.png`">


    </a-assets>

    <!-- Lights -->
    <a-entity light="type: ambient; color: #ffffff; intensity: 1"></a-entity>
    <a-entity light="type: directional; color: #fafafa; intensity: .8; castShadow: true" position="0 7.5 10" rotation="0 0 -25"></a-entity>

    <!-- Components depending on assets loading -->
    <template v-if="allAssetsLoaded">
      <TheOffice />
    </template>

    <!-- Camera Rig -->
    <TheCameraRig :allAssetsLoaded="allAssetsLoaded"/>
  </a-scene>
</template>

<style scoped>
:deep(.a-enter-vr-button) {
  display: none !important;
}
</style>