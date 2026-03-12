<script setup>
  import { ref, watch } from 'vue';
  import '../aframe/disable-in-vr.js';
  import '../aframe/hide-in-vr.js';
  import '../aframe/simple-navmesh-constraint.js';
  import '../aframe/blink-controls.js';
  import '../aframe/physx-grab.js';

  defineProps({
    allAssetsLoaded: Boolean,
  });

  const rotationY = ref(0);
  const rotationTarget = ref(0);
  const rotationAngle = ref(90);

  function turnLeft() {
    rotationTarget.value += rotationAngle.value;
  };

  function turnRight() {
    rotationTarget.value -= rotationAngle.value
  };

  watch(rotationTarget, (newVal) => {
  const rig = document.getElementById('camera-rig');
  if (rig) {
    rig.setAttribute('animation', `property: rotation; to: 0 ${newVal} 0; dur: 500; easing: easeInOutQuad`);
  }
});

</script>

<template>
  <a-entity
    id="camera-rig"
    :rotation="`0 ${rotationY} 0`"
    movement-controls="enabled: true"
    disable-in-vr="component: movement-controls;"
    :animation="{
      property: 'rotation',
      to: `0 ${rotationTarget} 0`,
      dur: 500,
      easing: 'easeInOutQuad'
    }"
    @animationcomplete="rotationY = rotationTarget"
  >
    <a-entity
      id="head"
      camera
      position="0 1.65 0"
      cursor="rayOrigin: mouse; objects: .clickable"
    ></a-entity>
  </a-entity>

  <div>
    <button class="turn-btn-left" @click="turnLeft">←</button>
    <button class="turn-btn-right" @click="turnRight">→</button>
  </div>
</template>


<style scoped>
.turn-btn-left,
.turn-btn-right {
  position: fixed;
  top: 50%;
  transform: translateY(-50%);
  width: 64px;
  height: 64px;
  font-size: 32px;
  border: none;
  border-radius: 9999px;
  color: #fafafa;
  cursor: pointer;
  z-index: 100;
  background-color: rgba(0, 0, 0, 0.25);
}

.turn-btn-left {
  left: 5vw;
}

.turn-btn-right {
  right: 5vw;
}

.turn-btn-left:hover,
.turn-btn-right:hover {
  background-color: rgba(0, 0, 0, 0.5);
}
</style>