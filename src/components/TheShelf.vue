<script setup>
import { ref, onMounted } from 'vue';

import '../aframe/clickable.js'

import BaseBinder from './BaseBinder.vue';

const shelfColor = ref('#8e8e8e')

const binderProbability = ref(.7)
const binderWidth = ref(.08)
const binderSpacing = ref(.01)
const binderAmount = 22

const availableSpaceForBinders = binderAmount * (binderWidth.value + binderSpacing.value) + binderSpacing.value

const shelfHeight = ref(2.03)
const shelfDepth = ref(.45)
const plankThickness = ref(.02)
const bezelThickness = ref(.1)
const shelfsAmount = ref(4)

const shelfWidth = ref(availableSpaceForBinders + 2*plankThickness.value)

const isSortVisible = ref(false)

function showSort() {
    isSortVisible.value = true;
}

function hideSort() {
    isSortVisible.value = false;
}



</script>

<template>
    <a-entity>
        <a-entity
            id="shelf"
            class="clickable"
            clickable
            @click="showSort"
        >
            <a-box
                :width="shelfWidth"
                :height="bezelThickness"
                :depth="shelfDepth"
                :position="`0 ${bezelThickness/2} 0`"
                :color="shelfColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.5; metalness: 0.1"
            ></a-box>
            <a-box
                :width="shelfWidth"
                :height="bezelThickness"
                :depth="shelfDepth"
                :position="`0 ${shelfHeight -bezelThickness/2} 0`"
                :color="shelfColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.5; metalness: 0.1"
            ></a-box>

            <a-box
                :width="plankThickness"
                :height="shelfHeight - 2*bezelThickness"
                :depth="shelfDepth"
                :position="`${(shelfWidth - plankThickness)/2} ${shelfHeight/2} 0`"
                :color="shelfColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.5; metalness: 0.1"
            ></a-box>
            <a-box
                :width="plankThickness"
                :height="shelfHeight - 2*bezelThickness"
                :depth="shelfDepth"
                :position="`${-(shelfWidth - plankThickness)/2} ${shelfHeight/2} 0`"
                :color="shelfColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.5; metalness: 0.1"
            ></a-box>
            <a-box
                v-for="i in Math.floor(shelfsAmount + 1)"
                :width="shelfWidth - 2*plankThickness"
                :height="plankThickness"
                :depth="shelfDepth"
                :position="`0 ${bezelThickness + ((shelfHeight - 2*bezelThickness)/(shelfsAmount + 1) * (i-1)) } 0`"
                :color="shelfColor"
                shadow="cast: true; receive: true"
                material="roughness: 0.5; metalness: 0.1"
            >
                <a-entity>
                    <a-entity
                        v-for="j in binderAmount"
                    >
                        <BaseBinder
                            v-if="Math.random() < binderProbability"
                            :key="j"
                            :binderWidth="binderWidth"
                            :position="`${-availableSpaceForBinders/2 + (j-1)*(binderWidth + binderSpacing) + binderWidth/2 + binderSpacing} 0 0`"
                        />
                    </a-entity>    
                </a-entity>
            </a-box>
            <a-entity
            v-if="isSortVisible"
            position="0 1.65 1.575">

            <a-image
                width="1.6"
                height="0.576"
                src="#sort"
                look-at
                class="clickable"
                clickable
                @click.stop="hideSort"
            ></a-image>
        </a-entity>
        </a-entity>
    </a-entity>
</template>