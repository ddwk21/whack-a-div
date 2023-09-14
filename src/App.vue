<template>
  <h1>Whack-A-Div</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @score="recordScore"/>
  <p v-if="showResults">Reaction Time: {{ score }} ms</p>
</template>

<script>

import Block from './components/Block.vue'

export default {
  name: 'App',
  components: {
    Block
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
      this.showResults = false;
    },
    recordScore(reactionTime){
      this.score = reactionTime;
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
