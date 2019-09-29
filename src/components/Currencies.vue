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
export default {
    name: 'Currencies',
    data(){
        return {
            currencies:[]
        };
    },
    methods:{
        getCurrencies: function(){
           this.$http.get('https://localhost:9991/api/currencies').then(response => {
               //console.log(response);
               //console.log(response.data);
               this.currencies = response.body;
           }); 
        }
    }
}
</script>