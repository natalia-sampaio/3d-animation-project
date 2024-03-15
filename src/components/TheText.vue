<script setup lang="ts">
import { OrbitControls, Text3D } from '@tresjs/cientos';
import { TresCanvas } from '@tresjs/core'

const fontPath = 'https://raw.githubusercontent.com/Tresjs/assets/main/fonts/FiraCodeRegular.json'
</script>

<template>
  <TresCanvas
    shadows
    alpha
  >
  <TresPerspectiveCamera :position="[5, 5, 5]" />
    <OrbitControls />
    <Suspense>
      <Text3D :font="fontPath" />
    </Suspense>
    <TresAmbientLight
      :intensity="0.5"
      color="red"
    />
    <TresGridHelper />
  </TresCanvas>
</template>