<template>
  <div class="whackamole">
    <h1 class="logo">
      Whack-a-mole!
    </h1>
    <button
      class="start-game"
      v-on:click="startGame"
    >
      Start Game
    </button>
    <div class="counters-container">
      <Counter label="Score:" v-bind:value="score" />
      <Counter label="High Score:" v-bind:value="highScore" />
      <Counter label="Timer" v-bind:value="timer" />
    </div>
    <Moles
      v-bind:moleData="moles"
      v-bind:gameActive="gameActive"
      v-on:whack="handleMoleWhack"
    />
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
  data: function() {
    return {
      score: 0,
      highScore: 0,
      timer: 20,
      moles: [false, false, false, false],
      gameActive: false,
    };
  },
  methods: {
    resetState: function() {
      this.score = 0;
      this.timer = 20;
      this.moles = [false, false, false, false];
    },
    startGame: function() {
      this.resetState();
      this.gameActive = true;
      this.startTimer();
      this.startMoles();
    },
    endGame: function() {
      this.gameActive = false;
      this.stopTimer();
      this.stopMoles();
    },
    startTimer: function() {
      this.timerId = setInterval(() => {
        this.decrementTime();
      }, 1000);
    },
    decrementTime: function() {
      this.timer--;
      if (this.timer === 0) {
        this.endGame();
      }
    },
    stopTimer: function() {
      clearInterval(this.timerId);
    },
    startMoles: function() {
      this.moleInterval = setInterval(this.activateRandomMole.bind(this), 500);
    },
    stopMoles: function() {
      clearInterval(this.moleInterval);
    },
    activateRandomMole: function() {
      const randomMoleIndex = Math.floor(Math.random() * this.moles.length);
      if (!this.moles[randomMoleIndex]) {
        this.activateMole(randomMoleIndex);
      }
    },
    toggleMole: function(moleId, shouldShow) {
      const moles = this.moles.slice();
      moles[moleId] = shouldShow;
      this.moles = moles;
    },
    activateMole: function(moleId) {
      this.toggleMole(moleId, true);
      setTimeout(() => this.deactivateMole(moleId), 1500);
    },
    deactivateMole: function(moleId) {
      this.toggleMole(moleId, false);
    },
    handleMoleWhack: function(moleId) {
      this.score = this.score + 1;
      this.deactivateMole(moleId);
    },
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
