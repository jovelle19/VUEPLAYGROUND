<template>
  <div class="container">
    <AppNavbar></AppNavbar>
    <AppContent></AppContent>
    <AppFooter></AppFooter>
  </div>
</template>

<script>
import AppNavbar from "../components/app/Navbar.vue";
import AppContent from "../components/app/Content.vue";
import AppFooter from "../components/app/Footer.vue";

export default {
  components:{
    AppNavbar,
    AppFooter,
    AppContent
  },
  data(){
    return{

    }
  }
}
</script>

<style>
.container {
  display: block;
  justify-content: center;
}

</style>
