<template>
  <h1>Reaction Timer Game</h1>

  <button @click="start" :disabled="isPlaying">Play</button>

  <Block :delay="delay" v-if="isPlaying" @game-end="gameEnd" />
  <Result :score="score" v-if="!isPlaying && score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
    };
  },

  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
    },
    gameEnd(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.delay = null;
    },
  },
};
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
