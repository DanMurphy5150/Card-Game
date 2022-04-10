<template>
  <div class="game-board">
    <game-card
      v-for="data in selectedThemeData[0]"
      :key="data.id"
      @click="$emit('game-start', data.id)"
    >
      <img v-bind:src="data.img" />
    </game-card>
  </div>
</template>

<script>
import GameCard from './GameCard.vue';

export default {
  components: { GameCard },
  props: ['selectedThemeData'],
  data() {
    return {
      clickedCards: [],
    };
  },
};
</script>

<style scoped>
img {
  margin: auto;
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
