<script setup>
  import { ref } from 'vue';

  defineProps({
    loaded: Boolean,
  });

  const showOnboarding = ref(true);

  function enterScene() {
    showOnboarding.value = false;
    if (AFRAME.utils.device.checkHeadsetConnected() && !AFRAME.utils.device.isMobile()) {
      document.querySelector('a-scene').enterVR();
    }
    document.querySelector('a-scene').emit('enter-scene');
  }
</script>

<template>
  <div id="onboarding" v-if="showOnboarding">
    <div>
      <h1>Bureau Virtuel - BOB</h1>
      <p v-if="!loaded">chargement…</p>
      <button v-if="loaded" @click="enterScene()">Visitez le bureau virtuel</button>
    </div>
  </div>
</template>

<style scoped>
  h1 { font-size: 1.5rem }
  a {
    color: #eee;
    text-decoration: none;
  }
  #onboarding {
    position: absolute;
    top: 0;
    left: 0;
    background-color: #438d5a;
    color: #fafafa;
    width: 100vw;
    height: 100vh;
    padding: 1rem;
    font-family: avenir next, avenir, sans-serif;
    z-index: 10000;
    overflow: auto;
  }
  #onboarding > * {
    margin: 0 auto;
    max-width: 50rem;
    width: calc(100vw - 10rem);
    text-align: center;
    border-radius: 0.3rem;
    padding: 1rem;
    font-size: 1.3rem;
  }
  #onboarding button {
    font-size: 1.3rem;
    padding: 0.5rem 1rem;
    border-radius: 0.3rem;
    background-color: #fafafa;
    color: #1e1e1e;
    border: none;
    cursor: pointer;
  }
</style>