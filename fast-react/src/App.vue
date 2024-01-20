<template>
  <div>
    <h1>CLICK THE BOX ASAP</h1>

    <button @click="start" :disabled="isPlaying" >play</button>
    <Block v-if="isPlaying" :delay="delay" @end= "endGame"/>
    <Results v-if="showResult" :score="score"/>
  
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default({

  name: 'App',
  components: {Block, Results},
  data() {
    return{
      isPlaying: false,
      delay: 0,
      score: 0,
      showResult: false
    }
  },

  methods: {
    start() {
      this.delay= 2000 + Math.random() * 5000
      this.isPlaying= true
      this.showResult= false
    },
    endGame(reactionTime) {
      this.isPlaying= false
      this.score= reactionTime
      this.showResult= true
    }
  }

});
</script>

<style>
body {
  background-color: #ACE1AF;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #292828;
  margin-top: 60px;
}

button {
  background: #0faf87;
  color: white;
  border: black solid 1px;
  border-radius: 5px;
  padding: 8px 16px;
  font-size: 20px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  text-transform: uppercase;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
