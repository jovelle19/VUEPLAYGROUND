<template>
    <div class="container">
        <div class="wrapper">
            <CalendarMain></CalendarMain>
        </div>
    </div>
</template>


<script>
    import CalendarMain from "../../components/calendar/Main.vue";

    export default {
        components:{
            CalendarMain
        },
        data(){
            return{

            }
        }
    }
</script>


<style scoped>
    .container{
      width: 100%;
      margin: 50px auto; 
      padding: 0 50px;
    }
    .wrapper {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
    }
</style>