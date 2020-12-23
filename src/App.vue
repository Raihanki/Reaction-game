<template>
  <h1>Gaou Reaction Game</h1>
  <button @click="startGame" class="playButton" :disabled="isPlaying">play</button>
  <Block :delay="delay" v-if="isPlaying" @end="endGame"></Block>
  <Result :timeResult="score" v-if="gameOver"></Result>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      gameOver: false,
    }
  },
  methods: {
    startGame() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.gameOver = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.gameOver = true;
      this.isPlaying = false;
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
  color: #0d1c00;
  margin-top: 60px;
}
.playButton {
  padding: 10px 20px;
  color: white;
  border: none;
  background: #5bb75b;
  border-radius: 5px;
  font-size: large;
}
.playButton:hover {
  background: green;
}
.playButton:focus {
  outline-width: thin;
  outline-color: darkgreen;
}
.playButton[disabled] {
  opacity: 0.4;
  cursor: not-allowed;
}
</style>
