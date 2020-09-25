<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/Seal_of_the_Ministry_of_Public_Health_of_Thailand.svg.png" width="15%">
    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <covid />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import covid from './components/covid.vue'

export default {
  name: 'App',
  components: {
    //HelloWorld,
    covid
  },
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
