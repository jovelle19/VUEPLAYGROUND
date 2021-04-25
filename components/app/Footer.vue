<template>

    <footer>
        <p>  © 2021 | {{ author }}</p>
    </footer>

</template>


<script>
    export default{
        data(){
            return{
                author : "Jovelle"
            }
        }
    }
</script>


<style>
    footer{
        position: fixed;
        left: 0;
        bottom: 0;
        width: 100%;
        background: #eeeeee;
        padding: 10px;
        text-align:center
    }
</style>