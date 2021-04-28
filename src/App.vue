<template>
  <div id="app">
    <h1>Boo Calculator</h1>
    <Calculator msg="Calc-App"/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
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
h1{
  color: #f8f8f8;
  margin-bottom:100px;
}
</style>
