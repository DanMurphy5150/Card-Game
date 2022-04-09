<template>
  <header>
    <nav>
      <div class="title">
        <h1>Memory Game!!!</h1>
      </div>
      <div class="instructions">
        <p><b>Instructions:</b> {{ instructions }}</p>
      </div>
      <div class="scores">
        <ul>
          <li>Score: {{ score }}</li>
          <li>Highest Score: {{ highScore }}</li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  props: ['instructions', 'score', 'highScore'],
};
</script>

<style scoped>
header {
  width: 100%;
  height: 10rem;
  background-color: #907de3;
}
nav {
  height: 100%;
  display: flex;
  padding-left: 3%;
  justify-content: space-between;
  box-shadow: 0 5px 8px rgba(3, 44, 71, 0.588);
}

h1 {
  margin: 0;
  display: flex;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: block;
  margin-block-start: 20%;
}

li {
  font-size: 25px;
  margin: 2%;
  display: inline-block;
}

p {
  font-size: 30px;
}

.title {
  font-size: 30px;
  margin: 0;
  padding: 0;
  height: 100%;
  display: flex;
  justify-content: left;
  align-items: center;
}

.instructions {
  display: flex;

  align-items: center;
}
</style>
