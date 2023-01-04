<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block , Results },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
  }
},
  methods: {
    start(){
      this.delay = 1000 + Math.random() * 5000
      this.isPlaying = true
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

<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score"/>

</template>

<style>
#app{
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
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

@media screen and (max-width:450px) {
  .block{
    scale: 0.75;
    align-self: start;
  }
}
</style>
