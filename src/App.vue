<template>
  <h1> Ninja Reaction Timer </h1>
  <button class="btn" @click="start" :disabled="isPlaying">Play!</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Results v-if="showResults" :score="score"> </Results>
</template>

<script>
import Block from './components/block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start(){
      this.delay = 1000 + Math.random()*5000
      this.isPlaying = true
      console.log(this.delay)
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
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
  color: #2c3e50;
  margin-top: 60px;
}

.btn {
  width: 80px;
  height: 40px;
  background: #0faf87;
  border-radius: 10px;
}

.btn:hover{
  cursor: pointer;
  background: #0faf8771;;
}

.btn:disabled{
  background: #0faf87;
}
</style>
