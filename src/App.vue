<template>
  <div id="container" @contextmenu="handleContext">
    <h1>Reaction Time Game</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block @end="endGame" v-if="isPlaying" :delay="delay" />
    <Results v-if="showResults" :score="score" />
  </div>
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false
      this.isPlaying = true
    },
    endGame(time) {
      this.score = time
      this.isPlaying = false
      this.showResults = true
    },
    handleContext(e) {
      e.preventDefault()
    }
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
  user-select: none;
}
#container {
  width: 100%;
  height: 100vh;
}
button {
  background: #0faf87;
  color: #fff;
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
