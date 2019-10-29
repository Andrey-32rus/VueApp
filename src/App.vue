<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"><br/> -->
    <Aside @menu-choice="menuChoice"/>
    <div class="main">
      <Currencies v-if="mainElementKey === 'currencies'" url="/service/api/currencies" @req-time="reqTime"/>
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
  padding: 5px;
  width: 85vw;
  margin-left: 15vw;
}

@media screen and (max-width:479px) {
    /* Target portrait smartphones */
    .main{
      width: 75vw;
      margin-left: 25vw;
    }
}
</style>

<style>

html{
  height: 100%;
}

body{
  height: 100%;
  margin: 0;
}

#app {

  height: 100%;
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
