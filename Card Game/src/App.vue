<template>
  <nav-bar
    :instructions="gameInstructions"
    :score="currentScore"
    :highScore="highestScore"
  ></nav-bar>
  <base-button
    v-for="data in cardThemes"
    :key="data.id"
    :buttonText="data.name"
    @click="chooseTheme(data.id)"
  ></base-button>
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
    },
  },
};
</script>
<style scoped>
body {
  margin: 0;
}
</style>
