<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <!-- Block: Passes the delay prop -->
  <Block v-if="isPlaying" :delay="delay" @end-game="endGame" />
  <!-- Results: Passes the score prop -->
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  // Name your App and register you components
  name: 'App',
  components: {
    Block,
    Results,
  },
  // Usually set this as a starting point for your data
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  // These help change your data or do something with the data
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000 // a random number between 0 - 5000 milliseconds;
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false;
      this.showResults = true;
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
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
