<template>
  <div class="whackamole">
    <h1 class="logo">
      Whack-a-mole!
    </h1>
    <button class="start-game">
      Start Game
    </button>
    <div class="counters-container">
      <Counter></Counter>
      <Counter></Counter>
      <Counter></Counter>
    </div>
    <Moles></Moles>
  </div>
</template>

<script>
import Counter from './components/Counter';
import Moles from './components/Moles';

export default {
  name: 'App',
  components: {
    Counter,
    Moles,
  },
};
</script>

<style>
.whackamole {
  font-family: 'Bungee', sans-serif;
  max-width: 960px;
  margin: auto;
  text-align: center;
}

.start-game {
  font-family: 'Bungee', sans-serif;
  padding: 20px;
  border-radius: 3px;
  border: 0;
  background-color: #52b1d6;
  color: #fff;
  font-size: 1em;
  cursor: pointer;
}

.counters-container {
  display: flex;
  justify-content: space-evenly;
}

p {
    font-size: 40px;
    margin: 0px
}
</style>
