<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"><br/> -->
    <Currencies url="https://192.168.1.101:9991/api/currencies" @req-time="reqTime"/>
    <p v-if="requestMilliseconds !== -1">Время выполнения запроса: {{this.requestMilliseconds}}ms</p>
  </div>
</template>

<script>
import Currencies from './components/Currencies'

export default {
  components: {
    Currencies
  },

  data(){
    return{
      requestMilliseconds: -1,
    };
  },

  methods:{
    reqTime(milliseconds){
      //console.log(milliseconds);
      this.requestMilliseconds = milliseconds;
    }
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
  /* margin-top: 60px; */
}

.w100{
    width: 100%;
}

.h100{
    height: 100%;
}

p{
  font-weight: bold;
}

</style>
