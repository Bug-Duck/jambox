<template>
  <div>
    <div class="flex flex-row float-left">
      <Mic v-if="micFlag" @click="micFlag = false" class="mx-10 my-5" />
      <MicOff v-else @click="micFlag = true" class="mx-10 my-5" />
      <Ear v-if="earFlag" @click="earFlag = false" class="mx-10 my-5" />
      <EarOff v-else @click="earFlag = true" class="mx-10 my-5" />
    </div>
    <div class="flex flex-row float-right">
      <Pause v-if="playFlag" @click="playFlag = false" class="mx-36 my-5" />
      <Play v-else @click="playFlag = true" class="mx-36 my-5" />
    </div>
  </div>
</template>

<script setup lang="ts">
import {
  Mic, MicOff,
  Ear, EarOff,
  Play, Pause,
} from 'lucide-vue-next';

const micFlag = ref(true)
const earFlag = ref(true)
const playFlag = ref(false)
</script>