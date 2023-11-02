<template>
  <div class="w-full h-screen font-extrabold text-6xl flex justify-center items-center"  id="sectionToClick" v-if="showBlock" @click="stopTimer" :style="{ backgroundColor: randomHexColor, color: randomFontColor }">
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
      reactionTime: null
    }
  },
  mounted(){
    //console.log(this.delay)
    
    setTimeout(() => {
      this.showBlock = true;
      this.randomHexColor = this.generateRandomColor();
      //randomHexColor = this.randomHexColor
      this.randomFontColor = this.generateRandomFontColor(this.randomHexColor)
      //console.log(this.randomHexColor)
      //console.log(this.randomFontColor)
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
      //console.log(this.reactionTime)
      this.$emit('end', this.reactionTime)
    },
    generateRandomColor(){
      const letters = '0123456789ABCDEF';
      let color = '#';
      for (let i = 0; i < 6; i++) {
          color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
      
    },
    generateRandomFontColor(color){
      return '#' + ("000000" + (0xFFFFFF ^ parseInt(color.substring(1),16)).toString(16)).slice(-6);
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
