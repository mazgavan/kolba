<template>
  <section class="home">
    <Header />
    <Greeting></Greeting>
    <Cases />
    <Footer />
  </section>
</template>

<script lang="ts" setup>
import { defineComponent } from "vue";

import Greeting from "@/components/pages/Main/GreetingView.vue";
import Cases from "@/components/pages/Main/CasesView.vue";
import Header from "@/components/HeaderVue.vue";
import Footer from "@/components/FooterVue.vue";
</script>
