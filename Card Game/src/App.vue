<template>
  <nav-bar
    :score="score"
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
    @game-start="gameStart"
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
      score: 0,
      highestScore: 0,
      cardThemes: CardThemes,
      selectedThemeData: [],
      clickedCards: [],
    };
  },
  methods: {
    chooseTheme(themeId) {
      this.selectedThemeData.push(this.cardThemes[themeId].data);
      this.gameStarted = !this.gameStarted;
      this.gameInstructions =
        'Click the cards below, but be careful not to click the same card twice...';
    },
    shuffleCards() {
      this.selectedThemeData[0].sort(function () {
        return 0.5 - Math.random();
      });
      console.log('shuffle');
    },
    gameStart(cardId) {
      if (this.clickedCards.indexOf(cardId) !== -1) {
        this.gameInstructions =
          'Sorry you have already selected that card...Try again?';
        this.clickedCards = [];
        this.score = 0;
      } else if (this.clickedCards.length < 9) {
        this.clickedCards.push(cardId);
        this.score++;
        this.gameInstructions = 'Nice Selection!! Keep going!!';

        this.checkHighScore();
        this.shuffleCards();
      } else {
        this.gameInstructions =
          'Winner, Winner, Chicken Dinner! Wanna try agian? Try a different theme...';
        this.highestScore = 10;
        this.score = 0;
      }
    },
    checkHighScore() {
      if (this.score > this.highestScore) {
        this.highestScore = this.score;
      }
    },
    resetGameBoard() {
      this.score = 0;
      this.gameStarted = false;
      this.selectedThemeData = [];
      this.clickedCards = [];
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
