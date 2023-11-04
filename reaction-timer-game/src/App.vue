<template>
  <div v-if="showWelcomeScreen" @mousedown="hideAndStart" class="h-screen flex items-center justify-center px-10 flex-col flex-wrap">
    <span class="text-center">
      <p class="text-xl md:text-3xl font-bold py-5">Welcome to the Reaction App!</p>
      <p class="text-normal font-bold md:text-2xl pb-5">Rules of the game</p>
      <p class="text-sm md:text-normal lg:text-xl">To start the game you have to click Play button</p>
      <p class="text-sm md:text-normal lg:text-xl">When the game starts, be prepared to click or tap as quickly as you can when you see the background color changes</p>
      <p class="text-sm md:text-normal lg:text-xl">Your reaction time will be measured in seconds</p>
      <p class="text-sm md:text-normal lg:text-xl">If you're ready tap or click anywhere on the screen to start the game!</p>
    </span> 
  </div>
  <div class="container mx-auto text-center pt-10" v-if="showGameScreen">
    <h1 class="text-6xl py-10"> Reaction timer</h1>
    <button @click="start" :disabled="isPlaying" class=" text-4xl rounded-full bg-slate-800 px-6 py-3 text-white ">Play</button>
    <p class="text-4xl py-10" v-if="isPlaying">Wait for it...</p>
    <blockSection v-if="isPlaying" v-bind:delay="delay" @end="endGame"/>
    <!-- when you pass through $emit variable - in this case reactionTime you get by default access to this variable in function -->
    <!-- <p class="py-20 text-6xl" v-if="showResults">Reaction time {{ score }} seconds</p> -->
    <resultSection v-if="showResults" v-bind:score="score" />
  </div>
 
</template>

<script>

import blockSection from './components/blockSection.vue'
import resultSection from './components/resultSection.vue'

export default {
  components: {
    blockSection,
    resultSection
},
  data(){
    return{
      showWelcomeScreen: true, 
      showGameScreen: false,
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    hideAndStart(){
      this.showWelcomeScreen = false
      this.showGameScreen = true
    },
    start(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false
    },
    endGame(reactionTime){

      this.score = reactionTime
      this.score = this.score / 1000
      //console.log(this.score)
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app{
  font-family: 'Courier New', Courier, monospace;
}




</style>
