<template>
  <v-app>
    <v-app-bar app color="black align-center" dark prominent>
      
        <v-img
          alt="Vuetify Logo"
          height="140"
          class="my-5"
          contain
          src="https://icons.iconarchive.com/icons/paomedia/small-n-flat/1024/lightning-icon.png"
        />
    </v-app-bar>

    <v-main class="yellow">
      <Calculator />
    </v-main>
  <v-btn color="success">text</v-btn>
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

.v-input input {
  font-size: calc(50px + 1vw);
  max-height: 80px;
  padding: 5vw;
}
.v-input {
  border-radius: 15px;
}
.v-input__slot.white {
  padding: 10px;
}
.v-select__selection {
  text-align: right;
  width: 100%;
  color:white !important;
  font-weight: 500;
  font-size: 24px;
  padding: 5px;
}
.v-select input {
  max-height: 30px;
  padding: 5px;
}
.v-messages__message {
 font-size: calc(16px + 1vw);
 padding: 5px;
 text-align:right;
 line-height: 16px;
 direction:ltr;
}
</style>
