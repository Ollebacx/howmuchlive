<template>
  <v-app>
    <v-main>
      <v-container class="pa-0">
        <v-row>
          <v-col cols="12" class="landing"
            ><div class="dotted-bg">
              <h1 class="brand">LifePay Calculator</h1>
              <h2 class="subtitle">Life is time. Time is gold.</h2>
            </div>
          </v-col>
          <v-col>
            <Calculator />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "App",

  components: {
    Calculator,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
#app {
  /* background-color: #e9edf1; */
  font-family: "Roboto", sans-serif;
  font-size: calc(12px + 0.33vw);
  color: blue;
}
.landing {
  width: 100vw;
  height: 150px;
  border-radius: 0 0 40px 40px;
  text-align: center;
  background-image: linear-gradient(
    45deg,
    #009ad9 3%,
    #1b5aec 30%,
    #361bff 56%,
    #8357ff 94%
  );
  z-index: 1;
}
.dotted-bg {
  width: 100%;
  height: 150px;
  position: absolute;
  top: 0;
  left: 0;
  background-image: radial-gradient(rgba(255, 255, 255, 0.15) 1px, transparent 0);
  background-size: 35px 35px;
  background-repeat: initial;
}
h1.brand {
  padding: .8em 2vw 0 2vw;
  color: white;
  font-size: 3em;
  line-height: 1.6;
  font-weight: 800;
}
h2.subtitle {
  padding: 0 2vw 0 2vw;
  color: white;
  font-size: 2.5em;
  line-height: 1;
  font-weight: 300;
}
/* .navbar {
  height: 10vh !important;
  line-height: 50px !important;
  justify-content: center;
  align-items: flex-end;
} */
</style>
