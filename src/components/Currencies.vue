<template>
<div id="Currencies">
    <button @click="getCurrencies">Начать</button>
    <table>
        <thead>
            <tr>
                <th>Id</th>
                <th>Name</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="cur in currencies" :key="cur.Id">
                <td>{{cur.Id}}</td>
                <td>{{cur.Name}}</td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
// import axios from 'axios'

export default {
    name: 'Currencies',
    data(){
        return {
            currencies:[]
        };
    },
    methods:{
        getCurrencies: function(){
           this.$http.get('https://localhost:5001/api/currencies').then(response => {
               console.log(response);
               console.log(response.data);
               this.currencies = response.data;
           }); 
        }
    }
}
</script>