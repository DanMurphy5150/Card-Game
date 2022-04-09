<template>
  <nav-bar
    :score="currentScore"
    :highScore="highestScore"
    :instructions="gameInstructions"
  ></nav-bar>
  <div v-if="!gameStarted">
    <base-button
      v-for="data in cardThemes"
      :key="data.id"
      :buttonText="data.name"
      @click="chooseTheme(data.id)"
    ></base-button>
  </div>
  <div>
    <base-button v-if="gameStarted" @click="resetGameBoard"
      >Choose a Different Theme?</base-button
    >
  </div>
  <game-board
    v-if="gameStarted"
    :selectedThemeData="selectedThemeData"
  ></game-board>
</template>

<script>
import GameBoard from './components/GameBoard.vue';
import NavBar from './components/NavBar.vue';
import CardThemes from './data/cardThemes.json';
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
      cardThemes: CardThemes,
      selectedThemeData: [],
    };
  },
  methods: {
    chooseTheme(themeId) {
      this.selectedThemeData.push(this.cardThemes[themeId].data);
      this.gameStarted = !this.gameStarted;
      this.gameInstructions =
        'Click the cards below, but be careful not to click the same card twice...';
    },

    resetGameBoard() {
      this.currentScore = 0;
      this.gameStarted = false;
      this.selectedThemeData = [];
      this.gameInstructions =
        'Click a button below to select a memory card game theme...';
    },
  },
};
</script>
<style scoped>
body {
  margin: 0;
}
</style>
