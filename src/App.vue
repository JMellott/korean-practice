<template>
  <NumberPractice/>
  <ClockPractice />
</template>

<script>
import NumberPractice from './components/NumberPractice.vue';
import ClockPractice from './components/ClockPractice.vue';

export default {
  name: 'App',
  components: {
    NumberPractice,
    ClockPractice
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
