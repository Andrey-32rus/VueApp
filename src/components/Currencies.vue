<template>
<div id="Currencies">
    <div v-if="isLoading === true" class="img-container">
        <img src="../assets/loading.gif" class="img" alt="Loading..."/>
    </div>
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
                <tr v-for="(cur, index) in currencies" :key="cur.ID" @click="rowClick(index)">
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
            var startTime = Date.now();

            if(this.currencies.length == 0){
                this.isLoading = true;
            }

            axios.get(this.url)
            .then(response => {
                if(response.status == 200){
                    //console.log(response);
                    this.currencies = response.data;
                    this.$emit('req-time', Date.now() - startTime);
                }
                else{
                    alert(response.status);
                }
            })
            .catch(error => {
               alert(error);
            })
            .finally(() => {
                //this.isLoading = false;
            }); 
        },

        rowClick(index){
           this.currencies.splice(index, 1);
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
    margin-top: 1.25rem;
}

tbody tr {
    cursor: pointer;
}

button {
    cursor: pointer;
}

.img{
    width: 100%;
    max-height: 93vh;
}

.img-container{
    width: 100%;
    margin: 0 auto;
    height: 93vh;
}

</style>