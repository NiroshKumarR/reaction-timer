<template>
  <h1 style='color:purple'>ReflexClick</h1>
  <button @click="start" :disabled='isPlaying'>Shoot-Play</button>
  <Block v-if="isPlaying" :delay="delay" @end='endgame' />
  <Results v-if="showResults" :score="score"/>
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results},
  data() {
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  }, 
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endgame(time){
      this.score = time
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
  color: rgb(15, 15, 15);
  margin-top: 60px;
}
button{
  background: red;
  color:white;
  border:none;
  padding:8px 16px;
  border-radius:4px;
  font-size:16px;
  letter-spacing:1px;
  cursor:pointer;
  margin:10px;
}
button[disabled]{
  opacity:0.2;
  cursor:not-allowed;
}
</style>
