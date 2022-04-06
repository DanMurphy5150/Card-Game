<template>
  <div class="game-board">
    <game-card v-for="data in cardData" :key="data.id">
      <img v-bind:src="'/src/assets/images/cats/' + data.img" />
    </game-card>
  </div>
</template>

<script>
import CardThemes from '../data/cardThemes.json';
import GameCard from './GameCard.vue';

export default {
  components: { GameCard },
  data() {
    return {
      cardData: CardThemes,
    };
  },
  methods: {},
};
</script>

<style scoped>
img {
  margin: 1rem auto;
  width: 99%;
  height: 100%;
  border-radius: 12px;
  text-align: center;
}

.game-board {
  height: 100%;
  display: flex;
  flex-flow: row wrap;
  padding: 20px;
  justify-content: space-around;
  align-content: flex-start;
  overflow: auto;
}
</style>
