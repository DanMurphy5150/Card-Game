<template>
  <nav-bar
    :score="score"
    :highScore="highestScore"
    :instructions="gameInstructions"
  ></nav-bar>
  <div class="button-bar" v-if="!gameStarted">
    <base-button
      v-for="data in cardThemes"
      :key="data.id"
      :buttonText="data.name"
      @click="chooseTheme(data.id)"
    ></base-button>
  </div>
  <div class="button-bar">
    <base-button v-if="gameStarted" @click="resetGameBoard"
      >Choose a Different Theme?</base-button
    >
  </div>
  <transition>
    <game-board
      v-if="gameStarted"
      :selectedThemeData="selectedThemeData"
      @game-start="gameStart"
    ></game-board>
  </transition>
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
        'Click the cards below, but be careful not to click the same card twice. The cards will shuffle once you click them...';
    },
    checkHighScore() {
      if (this.score > this.highestScore) {
        this.highestScore = this.score;
      }
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
          'Winner, Winner, Chicken Dinner! Wanna try again? Try a different theme...';
        this.highestScore = 10;
        this.score = 10;
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
<style>
body {
  margin: 0;
  background-color: rgb(181, 209, 248);
}

.button-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 8px;
  padding: 8px;
}

.v-enter-from {
  opacity: 0;
  transform: translateX(50px) translateY(40px);
}

.v-enter-active {
  transition: all 0.6s ease-in-out;
}

.v-enter-to {
  opacity: 1;
  transform: translateX(0) translateY(0);
}
</style>
