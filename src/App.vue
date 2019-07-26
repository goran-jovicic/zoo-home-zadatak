<template>
  <div id="app">
    <AnimalList/>
  </div>
</template>

<script>
import AnimalList from './components/AnimalList'

export default {
  components: {
    AnimalList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
