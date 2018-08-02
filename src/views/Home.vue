<template>
    <div class="wrapper">
         <Claim />
       <SearchInput />
           <!--
           <ul>
               <li v-for="item in results" :key="item.data[0].nasa_id">{{item.data[0].description}}</li>
           </ul>
-->
            </div>

</template>

<script>
    import axios from 'axios';
    import  debounce  from 'lodash.debounce';
    import Claim from '@/components/Claim';
    import SearchInput from '@/components/SearchInput';
    
    const API = 'https://images-api.nasa.gov/search';
    export default {
        name: 'Home',
        components:{
            Claim,
            SearchInput
        },
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
        justify-content: center;
        margin: 0;
        padding: 30px;
        width: 100%;
        background-image: url('../assets/heroimage.jpg');
        background-repeat: no-repeat;
        background-size: cover;
        background-position: 80% 0;
        height: 100vh;
        
    }
  
</style>
