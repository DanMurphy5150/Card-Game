<template>
  <button @click="readData">Click Me for data</button>
  <ul>
    <li v-for="data in cardData" :key="data.id">
      <img v-bind:src="'/src/assets/images/cats/' + data.img" />
    </li>
  </ul>
</template>

<script>
import CardThemes from '../data/cardThemes.json';

export default {
  data() {
    return {
      cardData: CardThemes,
    };
  },
  methods: {
    readData() {
      console.log(this.CardThemes);
    },
  },
};
</script>
