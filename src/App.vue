<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
  <!-- <p v-if="showResults">Reaction Time: {{ score }} ms</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying: false,
      delay : null,
      score : null,
      showResults: false
    }
  },
  methods: { 
    start(){
      this.isPlaying = true,
      this.showResults = false,
      this.delay = 2000 + Math.random() * 5000
    },
    endGame(reactionTime){
      this.score = reactionTime,
      this.isPlaying = false,
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background-color: #444fff;
  border: none;
  color: white;
  padding: 20px 40px;
  text-align: center;
  font-size: 20px;
  margin: 4px 2px;
  cursor: pointer;
}
</style>
