<template>
  <button>
    <slot>{{ buttonText }}</slot>
  </button>
</template>

<script>
export default {
  props: ['buttonText'],
};
</script>

<style scoped>
button {
  font: inherit;
  font-size: 25px;
  border: 1px solid #360032;
  background-color: #360032;
  color: white;
  padding: 0.5rem 2rem;
  height: 50px;
  margin: 5px;
  cursor: pointer;
  box-shadow: 0 5px 8px rgba(2, 16, 26, 0.707);
}

button:hover,
button:active {
  background-color: #97058d;
  border-color: #5c0556;
}
</style>
