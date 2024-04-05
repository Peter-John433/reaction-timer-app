<template>
    <div class="container">
        <div class="block" v-if="showBlock" @click="stopTimer">
            tap this box as  fast as you can!
        </div>
    </div>
</template>

<script>
 export default{
   props:['delay'],
   data(){
      return{
        showBlock: false,
        timer: null,
        reactionTime: 0
      }
   },

   mounted(){
      setTimeout(() => {
        this.showBlock = true
        this.startTimer()
      }, this.delay)
   },
   methods:{
     startTimer(){
        this.timer = setInterval(() => {
            this.reactionTime += 10
        }, 10) 
     },
     stopTimer(){
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
     }
   }
 }
</script>

<style scoped>
  .block{
    width: 300px;
    padding: 100px 0;
    text-align: center;
    text-transform: capitalize;
    font-size: 16px;
    background-color: navy;
    color: white;
    text-shadow: 1px 1px 2px 3px red;
    margin: 40px auto;
    border-radius: 20px;
    box-shadow: 2px 2px 3px 5px gray;
  }
</style>
