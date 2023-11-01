<template>
  <div class="w-full h-screen text-black font-extrabold text-4xl bg-green-400 flex justify-center items-center" id="sectionToClick" v-if="showBlock" @click="stopTimer">
    Click me!
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data(){
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted(){
    //console.log(this.delay)
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      console.log(this.reactionTime)
    }
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#sectionToClick{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
