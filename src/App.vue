<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"><br/> -->
    <Aside @menu-choice="menuChoice"/>
    <div class="main">
      <Currencies v-if="mainElementKey === 'currencies'" url="http://192.168.1.101:9990/api/currencies" @req-time="reqTime"/>
      <p v-if="requestMilliseconds !== -1">Время выполнения запроса: {{this.requestMilliseconds}}ms</p>
    </div>
  </div>
</template>

<script>
import Currencies from './components/Currencies'
import Aside from './components/Aside'

export default {
  components: {
    Currencies,
    Aside,
  },

  data(){
    return{
      requestMilliseconds: -1,
      mainElementKey: String,
    };
  },

  methods:{
    reqTime(milliseconds){
      //console.log(milliseconds);
      this.requestMilliseconds = milliseconds;
    },
    menuChoice(key){
      this.mainElementKey = key;
    }
  }
}
</script>

<style scoped>
.main{
  width: 85vw;
}

@media screen and (max-width:479px) {
    /* Target portrait smartphones */
    .main{
      width: 75vw;
    }
}
</style>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex
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
