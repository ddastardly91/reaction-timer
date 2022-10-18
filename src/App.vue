<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame" />

  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.trunc(Math.random() * 8000);
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  padding: 10px 45px;
  border-radius: 25px;
  border: 1px solid #333;
}

button:hover {
  background-color: #42d392;
  color: white;
}

button:disabled {
  border: none;
  background-color: #999;
  color: #888;
}
</style>
