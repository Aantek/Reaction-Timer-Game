<template>
  <p class="text-6xl py-10">{{ score }} seconds</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{

        }
    },
    mounted(){
        //console.log("Component mounted");
    }
}
</script>

<style>

</style>