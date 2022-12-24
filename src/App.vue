<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null
  }
},
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
    }
  }
}
</script>

<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p>Reaction time {{score}} ms</p>

</template>

<style>
#app{
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button{
  background: #0faf87;
  border: none;
  border-radius: 5px;
  color: white;
  padding: 10px 30px;
}

button:disabled{
  background:rgba(0, 255, 136, 0.5);
}
</style>
