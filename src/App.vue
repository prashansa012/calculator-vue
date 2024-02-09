<template>
 <div id="app">
  <h1></h1>
  <calculater/>
 </div>
</template>

<script>
import Calculater from './components/Calculater.vue'

export default {
  name: 'App',
  components: {
    Calculater
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
