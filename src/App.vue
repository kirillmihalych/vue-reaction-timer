<template>
  <h1>Click Reaction Timer</h1>
  <button @click="start" v-bind:disabled="isPlaying">play</button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    },
  },
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
  background: crimson;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  margin: 10px;
  letter-spacing: 1px;
  font-size: 16px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
