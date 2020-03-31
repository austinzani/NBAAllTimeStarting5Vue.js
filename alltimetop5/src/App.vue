<template>
  <div id="app">
    <h1>Create your all time NBA Starting 5</h1>
    <h3>You have a total of $15 to assemble your lineup</h3>
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

#app h1{
  color: whitesmoke;
}

body {
  background: blue;
  background: radial-gradient(circle, rgba(14,99,235,1) 50%, rgba(0,61,158,1) 100%);
}

h3{
  color: whitesmoke;
}
</style>
