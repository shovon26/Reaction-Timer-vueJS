<template>
  <p> Reaction time: {{ score }}</p>
  <p class="rank"> {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank: null
        }
    },
    mounted(){
        if(this.score < 1000){
            this.rank = 'Ninja Fingure'
        }
        else if(this.score < 2000){
            this.rank = 'Rapid Reflexes'
        }
        else{
            this.rank = 'Slower...'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: aqua;
        font-weight: bold;
    }
</style>