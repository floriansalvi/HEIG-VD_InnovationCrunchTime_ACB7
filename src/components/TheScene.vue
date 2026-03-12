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
    
    :webxr="`
      requiredFeatures: local-floor;
      referenceSpaceType: local-floor;
      optionalFeatures: dom-overlay;
      overlayElement: ${overlaySelector};
    `"
    vr-mode-ui="enabled: true"
    xr-mode-ui="XRMode: xr"

    outline
    simple-grab
  >

    <!-- Assets -->
    <a-assets @loaded="allAssetsLoaded = true">
      <a-asset-item id="info-sign" src="assets/info-sign.glb"></a-asset-item>
      <a-asset-item id="plant" src="assets/plant.glb"></a-asset-item>
      <a-asset-item id="computer" src="assets/computer.glb"></a-asset-item>

      <img id="texture-floor" :src="`assets/texture-floor.jpg`">
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