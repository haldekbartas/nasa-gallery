<template>
    <div class="claimWrapper">
        <h1 class="claim">SPACER </h1>
                <p class="subclaim" >
                    Begin your journey through our amazing galaxy, and discover places you never even heard of.
                </p  >
                <p class="subclaim">
                    Type anything space-related to take off into space.
                </p>
        
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
    .claimWrapper{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .claim{
        font-size: 50px;
            }
    .subclaim{
        margin: 25px 0 0 0;
        font-size: 13px;
        
    }
</style>
