<script setup>
import { ref, onMounted } from 'vue';

import TheDesk from './TheDesk.vue';
import TheShelf from './TheShelf.vue';
import TheTable from './TheTable.vue'
import ThePrinter from './ThePrinter.vue';

const officeSize = ref(6)
const wallColor = ref('#fafafa')
const ceilingColor = ref('#ffffff')

</script>

<template>
    <a-entity>
        <a-plane
            id="floor"
            :width="officeSize"
            :height="officeSize"
            rotation="-90 0 0"
            position="0 0 0"
            material="src: #texture-floor; repeat: 4 4"
        ></a-plane>
        <a-plane
            id="ceiling"
            :width="officeSize"
            :height="officeSize"
            rotation="90 0 0"
            position="0 2.4 0"
            :color="ceilingColor"
        ></a-plane>
        <a-entity
            id="walls"
        >
            <a-plane
                id="wall-north"
                :width="officeSize"
                height="2.4"
                rotation="0 0 0"
                :position="`0 1.2 ${-officeSize/2}`"
                :color="wallColor"
            ></a-plane>
            <a-plane
                id="wall-south"
                :width="officeSize"
                height="2.4"
                rotation="0 180 0"
                :position="`0 1.2 ${officeSize/2}`"
                :color="wallColor"
            ></a-plane>
            <a-plane
                id="wall-east"
                :width="officeSize"
                height="2.4"
                rotation="0 -90 0"
                :position="`${officeSize/2} 1.2 0`"
                :color="wallColor"
            ></a-plane> 
            <a-plane
                id="wall-west"
                :width="officeSize"
                height="2.4"
                rotation="0 90 0"
                :position="`${-officeSize/2} 1.2 0`"
                :color="wallColor"
            ></a-plane> 
        </a-entity>
        <a-entity
            light="type: point;
                    color: #fcfae7;
                    castShadow: true;
                    intensity: 2;
                    distance: 10;
                    decay: 1"
            position="0 2.2 0">
        </a-entity>
        <a-image
            src="#logo-rp"
            :position="` ${officeSize/3} 1.75 ${-officeSize/2 + 0.001}`"
            width="1.72"
            height="1"
            material="transparent: true; alphaTest: 0.5"
        ></a-image>
        <TheDesk 
            :position="`0 0 ${-officeSize/2 + .6 + .4}`"
        />
        <TheShelf 
            :position="`${-officeSize/2 + .225} 0 0`"
            rotation="0 90 0"
        />
        <ThePrinter 
            :position="`0 0 ${officeSize/2 - .3}`"
            rotation="0 180 0"
        />
        <TheTable 
            :position="`${officeSize/2 - .3} 0 0`"
            rotation="0 -90 0"
        />
    </a-entity>
</template>