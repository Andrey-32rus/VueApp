<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"><br/> -->
    <Currencies url="https://localhost:9991/api/currencies"/>
  </div>
</template>

<script>
import Currencies from './components/Currencies'

export default {
  components: {
    Currencies
  },

  methods:{
    
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
