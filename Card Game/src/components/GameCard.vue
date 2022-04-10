<template>
  <div>
    <slot></slot>
  </div>
</template>

<style scoped>
div {
  margin: 1rem;
  max-width: 10rem;
  height: 250px;
  padding: 1rem;
  border-radius: 12px;
  overflow: hidden;
  background-color: rgb(6, 18, 11);
  box-shadow: 0 3px 8px rgba(17, 51, 72, 0.905);
}

div:hover,
div:active {
  background-color: #97058d;
  border-color: #5c0556;
  cursor: pointer;
}
</style>
