<template>
<div id="Currencies">
    <button @click="getCurrencies">Обновить</button>
    <table v-if="this.currencies.length != 0">
        <thead>
            <tr>
                <th>Id</th>
                <th>Code</th>
                <th>Name</th>
                <th>BaseRate</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="cur in currencies" :key="cur.ID">
                <td>{{cur.ID}}</td>
                <td>{{cur.CC}}</td>
                <td>{{cur.NM}}</td>
                <td>{{cur.BR}}</td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Currencies',
    data(){
        return {
            currencies:[]
        };
    },
    methods:{
        getCurrencies(){
            //console.log('getCurrencies');
            axios.get('https://localhost:9991/api/currencies')
           .then(response => {
               if(response.status == 200){
                    this.currencies = response.data;
               }
               else{
                   alert(response.status);
               }
               
           })
           .catch(error => {
               alert(error);
            }); 
        }
    },

    created(){
        //console.log('created');
        this.getCurrencies();
    }
}
</script>

<style scoped>
table {
    margin: auto;
}
</style>