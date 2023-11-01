<template>
  <div class="container mx-auto text-center pt-10">
    <h1 class="text-6xl py-10"> Reaction timer</h1>
    <button @click="start" :disabled="isPlaying" class=" text-4xl rounded-full bg-slate-800 px-6 py-3 text-white ">Play</button>
    <blockSection v-if="isPlaying" v-bind:delay="delay"/>
  </div>
</template>

<script>

import blockSection from './components/blockSection.vue'

export default {
  components: {
    blockSection,
  },
  data(){
    return{
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    start(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
    }
  }
}
</script>

<style>
#app{
  font-family: 'Courier New', Courier, monospace;
}
</style>
