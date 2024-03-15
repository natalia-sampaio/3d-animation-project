<script setup lang="ts">
import { OrbitControls, Stars, Text3D } from '@tresjs/cientos';
import { TresCanvas } from '@tresjs/core'
import gsap from 'gsap';
import { PerspectiveCamera } from 'three';
import { shallowRef, watch } from 'vue';

const fontPath = 'https://raw.githubusercontent.com/Tresjs/assets/main/fonts/FiraCodeRegular.json'

const cameraRef = shallowRef<PerspectiveCamera>();

watch(cameraRef, (camera) => {
  if(camera) {
    gsap.fromTo(
      camera.position, 
      {
        x: 0,
        y: 11,
        z: 0
      }, 
      {
        delay: 1,
        duration: 2,
        x: 0,
        y: 11,
        z: 11,
        ease: 'power3.out'
      }
    )
  }
})
</script>

<template>
  <TresCanvas>
  <TresPerspectiveCamera ref="cameraRef" :args="[45, 1, 0.1, 1000]" />
  <Stars />
    <OrbitControls />
    <Suspense>
      <Text3D :font="fontPath" :text="'welcome'" :size="0.8" center />
    </Suspense>
    <TresAmbientLight
      :intensity="0.5"
      color="red"
    />
    <TresGridHelper />
    <TresAxesHelper />
  </TresCanvas>
</template>