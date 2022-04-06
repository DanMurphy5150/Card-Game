<template>
  <nav-bar></nav-bar>
  <game-board></game-board>
</template>

<script>
import GameBoard from './components/GameBoard.vue';
import NavBar from './components/NavBar.vue';

export default {
  components: { GameBoard, NavBar },
};
</script>
<style scoped>
body {
  margin: 0;
}
</style>
