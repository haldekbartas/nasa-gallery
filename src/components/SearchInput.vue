
           <template>
      <div class="searchWrapper">
         
           <input 
           v-model:value="searchValue" 
           name="search" 
           type="text"
           @input="handleInput">
           <p>{{searchValue}}</p>
           </div>
 

</template>

<script>
    export default {
        name: 'Claim',
        data() {
            return {

            }
        },
        methods: {}

    }

</script>


<style lang="scss" scoped>
    .searchWrapper{
        margin-top: 50px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
      .search{
        display:flex;
        flex-direction: column;
        width: 250;
    }
    input{
        background:none;
        height: 30px;
        border:0;
        border-bottom: 1px solid black;
    }

</style>
