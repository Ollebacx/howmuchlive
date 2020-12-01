<template>
  <v-app>
    
    
    <v-main>
      <Calculator />
    </v-main>
  </v-app>
</template>

<script>
import Calculator from './components/Calculator.vue';

export default {
  name: "App",

  components: {
    Calculator
  },

  data: () => ({
    //
  })
};
</script>
<style>
#app {
background-color: white;
font-family: "Roboto", sans-serif;
font-size: calc(12px + 0.33vw);
color: #434547;
/* background-image: linear-gradient( 185deg, #2B315D 10%, #0D1428 100%); */
}
/* .navbar {
  height: 10vh !important;
  line-height: 50px !important;
  justify-content: center;
  align-items: flex-end;
} */


</style>
