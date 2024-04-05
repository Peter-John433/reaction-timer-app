<template>
  <div>
    <div class="cont-1 container">
      <h1>Reaction timer game</h1>
    </div>
    <div :class="button">
      <button :disabled="isPlaying" @click="start">play</button>
    </div>
     <Result v-if="showResult" :score="score" />
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  </div>
</template>

<script>
import Block from '@/components/Block.vue';
import Result from '@/components/Result.vue'
export default{
  components: { Block, Result },
   data(){
      return{
         button: 'btn',
         isPlaying: false,
         delay: null,
         score: null,
         showResult : false
      }
   },

   methods:{
     start(){
        this.isPlaying = true;
        this.delay = Math.random() * 5000 + 2000; // random time from 2 to 7 seconds
        this.showResult = false
     },
     endGame(reactionTime){
       this.score = reactionTime
       this.isPlaying = false
       this.showResult = true
     }
   }
}
</script>
