<template>
    <div>
        <div class="result">
            reaction time: <span> {{ score }} ms</span>
            <div class="rank">
                {{ rank }}
            </div>
        </div>
    </div>
</template>

<script>
 export default{
    props:['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score < 300 ){
            this.rank = ' very good'
        }else if(this.score < 600 ){
            this.rank = 'good'
        }else{
            this.rank = 'too fast...'
        }
    }
 }
</script>

<style scoped>
 .result{
    color: green;
    font-size: 18px;
    font-weight: bold;
    font-style: italic;
    text-align: center;
    margin: 1rem auto;
 }

 .result span{
    color: red;
 }

 .rank{
    color: navy;
    margin: 1rem auto;
    text-transform: capitalize;
 }
</style>