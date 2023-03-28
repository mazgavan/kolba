<template>
  <Header />
  <router-view />
</template>

<script lang="ts" setup>
import { defineComponent } from "vue";

import Header from "./components/HeaderVue.vue";
</script>

<style lang="scss">
@font-face {
  font-family: "Casio fx-9860GII";
  src: url("./assets/fonts/casio-fx-9860gii.ttf");
}

@font-face {
  font-family: "Crux";
  src: url("./assets/fonts/CoderCrux.ttf");
}
@font-face {
  font-family: "Valisca";
  src: url("./assets/fonts/Valisca.ttf");
}
@font-face {
  font-family: "Informal Roman";
  src: url("./assets/fonts/INFROMAN.TTF");
}
@font-face {
  font-family: "SF Pro Display";
  src: url("./assets/fonts/SFProDisplay-Regular.ttf");
}
@font-face {
  font-family: "RockStar";
  src: url("./assets/fonts/RockStar-Light.ttf");
}

:root {
  --dark-blue: #000071;
  --grey: #aaaaaa;
  --black: #000000;
  --white: #ffffff;
}
html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: var(--background);
}

*,
::after,
::before {
  box-sizing: border-box;
}

body {
  margin: 0;
}
</style>
