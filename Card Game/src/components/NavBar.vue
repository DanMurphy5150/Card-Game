<template>
  <header>
    <nav>
      <div class="title">
        <h1>Test your Memory!!!</h1>
      </div>
      <div class="instructions">
        <p>Instructions: Where will this sentence be displayed?</p>
      </div>
      <div class="scores">
        <ul>
          <li>Score:</li>
          <li>Highest Score:</li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<style scoped>
header {
  width: 100%;
  height: 10rem;
  background-color: #907de3;
}
nav {
  height: 100%;
  display: flex;
  padding-left: 5%;
  padding-right: 5%;
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
  margin-block-start: 45%;
}

li {
  margin: 1%;
  display: inline-block;
}

p {
  font-size: 25px;
}

.title {
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
