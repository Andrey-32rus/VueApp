<template>
  <div id="Aside">
      <p>Меню</p>
      <ul>
          <li @click="menuChoice('currencies')">Currencies</li>
          <li @click="menuChoice('none')">None</li>
      </ul>
  </div>
</template>

<script>
export default {

  data(){
    return{
      
    };
  },

  methods:{
    menuChoice(key){
        this.$emit('menu-choice', key);
    }
  }
}
</script>

<style scoped>
#Aside{
    width: 15vw;
    border: 1px solid black;
}

ul{
    margin-top: 1.5rem;
    padding: 0;
}
li{
    list-style-type: none;
    cursor: pointer;
    margin-top: 0.7rem;
}
p{
    font-weight: bold;
}

@media screen and (max-width:479px) {
    /* Target portrait smartphones */
    #Aside{
        width: 25vw;
    }
}

</style>