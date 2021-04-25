<template>
   <div class="top-navbar">
        <p class="title">NUXT-APP</p>
        <div>
            <a href="javascript:void(0)" class="active">CALENDAR</a>
            <a href="javascript:void(0)" class="">TASKS</a>
        </div>
   </div>
</template>

<script>
    export default
    {
        data(){
            return{
            
            }
        }
    }
</script>

<style>
    .title{
        display:block;
        float:left;
        color: white;
        padding: 14px;
    }
    .top-navbar {
        position: fixed;
        top:0;
        z-index:1;
        width: 100%;
        background:  #ef544b  ;
    }
    .top-navbar a{
        float: right;
        display:block;
        padding: 14px 16px;
        color: white;
        text-align:center;
        text-decoration: none;
        font-size: 17px;
    }
    .top-navbar :hover{
        float: right;
        display:block;
        color: yellow;
        text-align:center;
        text-decoration: none;
        font-size: 17px;
    }
    .top-navbar a.active{
        color: yellow;
        font-size: 17px;
    }
</style>