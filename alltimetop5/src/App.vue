<template>
  <div id="app">
    <h1>Create your all time NBA Starting 5</h1>
    <top-five/>
  </div>
</template>

<script>
import TopFive from './components/TopFive.vue'

export default {
  name: 'App',
  components: {
    TopFive
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
