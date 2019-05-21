<template>
  <div class="counter">
    <h2>{{ label }}</h2>
    <p>{{ value }}</p>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: ['label', 'value'],
};
</script>

<style>
.counter {
  border: 1px solid #000;
  margin-top: 20px;
  padding: 20px;
}

.counter h1,
.counter h2 {
  margin: 0;
}
</style>