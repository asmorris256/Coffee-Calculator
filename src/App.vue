<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <CoffeeCalculator msg="Ayooooo river"/>
    
  </div>
</template>

<script>
import CoffeeCalculator from './components/CoffeeCalculator.vue'

export default {
  name: 'app',
  components: {
    CoffeeCalculator
  }
}
</script>

<style>
#app {
  font-family: 'montserrat', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:black;
  margin-top: 60px;
}
</style>
