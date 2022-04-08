<template>
  <nav-bar
    :instructions="gameInstructions"
    :score="currentScore"
    :highScore="highestScore"
  ></nav-bar>
  <base-button v-if="!gameStarted" @click="chooseTheme">Cats</base-button>
  <game-board v-else></game-board>
</template>

<script>
import GameBoard from './components/GameBoard.vue';
import NavBar from './components/NavBar.vue';
import BaseButton from './components/BaseButton.vue';

export default {
  components: { GameBoard, NavBar, BaseButton },
  data() {
    return {
      gameStarted: false,
      gameInstructions:
        'Click a button below to select a memory card game theme...',
      currentScore: 0,
      highestScore: 0,
    };
  },
  methods: {
    chooseTheme() {
      this.gameStarted = !this.gameStarted;
    },
  },
};
</script>
<style scoped>
body {
  margin: 0;
}
</style>
