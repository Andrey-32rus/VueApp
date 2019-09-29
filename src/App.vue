<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png"><br/>
    <Currencies/>
  </div>
</template>

<script>
import Currencies from './components/Currencies'

export default {
  name: 'app',
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
