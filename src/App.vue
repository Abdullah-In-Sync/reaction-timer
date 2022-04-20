<template>
  <h1>Mars Reaction Timer</h1>
  <button class="btn" @click="start" :disabled="isPlaying">{{this.play}}</button>
  <Block v-if="isPlaying" :delay="delay" @end="showResult"/>
  <Results v-if="showScore" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: 'App',
  components: {Block, Results},
  data(){
    return {
    isPlaying:false,
    delay: null,
    score:null,
    showScore:false,
    play:"Play"

  }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random()*5000;
      this.isPlaying= true;
      console.log(this.delay);
      this.showScore = false;
    },
    showResult(countdown){
      this.showScore = true;
this.score = countdown;
this.isPlaying = false;
this.play = "Play Again";
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
.btn{
  border-radius: 3px;
  padding: 5px 10px;
  font-size: 20px;

  background-color: rgb(180, 255, 255);
}
</style>
