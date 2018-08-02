<template>
    <div class="wrapper">
         <h1>Nasa gallery app</h1>
         <div class="search">
          <label for="search">Search:</label>
           <input 
           v-model:value="searchValue" 
           name="search" 
           type="text"
           @input="handleInput">
           <p>{{searchValue}}</p>
           <ul>
               <li v-for="item in results" :key="item.data[0].nasa_id">{{item.data[0].description}}</li>
           </ul>
           </div>
            </div>

</template>

<script>
    import axios from 'axios';
    import  debounce  from 'lodash.debounce';
    
    const API = 'https://images-api.nasa.gov/search';
    export default {
        name: 'Home',
        data(){
            return{
                searchValue: '',
                results: [],
            }
        },
        methods: {
            handleInput: debounce(function() {
                console.log(this.searchValue);
                axios.get(`${API}?q=${this.searchValue}&media_type=image`)
                .then((response) =>{
                    console.log(response.data.collection.items);
                    this.results = response.data.collection.items;
                    
                })
                .catch((error) =>{
                       console.log(error);
                       });
            }, 500),
    },
    }

</script>


<style lang="scss" scoped>
    .wrapper {
        display:flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
        padding: 30px;
        width: 100%;
    }
    
    .search{
        display:flex;
        flex-direction: column;
        width: 250;
        label{
            font-family: Montserrat, sans-serif;
        }
    }
    input{
        height: 30px;
        border:0;
        border-bottom: 1px solid black;
    }

</style>
