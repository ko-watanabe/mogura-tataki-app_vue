<template>
  <div class="moles-container gameActive">
    <Mole></Mole>
    <Mole></Mole>
    <Mole></Mole>
    <Mole></Mole>
  </div>
</template>

<script>
import Mole from './Mole';

export default {
  name: 'Moles',
  components: {
    Mole,
  }
};
</script>

<style>
.moles-container {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  opacity: 0.5;
  transition: opacity 0.3s ease;
}

.moles-container.game-active {
  opacity: 1;
}
</style>
