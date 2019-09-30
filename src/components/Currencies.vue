<template>
<div id="Currencies">
    <div v-if="isLoading === true" class="w100 h100 loading"></div>
    <template v-else>
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
    </template>
</div>
</template>

<script>
import axios from 'axios'

export default {
    props:{
        url: String
    },
    data(){
        return {
            currencies:[],
            isLoading: true
        };
    },
    methods:{
        getCurrencies(){
            this.isLoading = true;
            //console.log('getCurrencies');
            axios.get(this.url)
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
            })
            .finally(() => {
                this.isLoading = false;
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

.loading {
    position: fixed;
    background-image: url('../assets/loading.gif');
    background-repeat: no-repeat;
    background-size: 100%;
}
</style>