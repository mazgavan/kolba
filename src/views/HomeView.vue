<template>
  <section class="home">
    <Greeting></Greeting>
    <Cases />
  </section>
</template>

<script lang="ts" setup>
import { defineComponent } from "vue";

import Greeting from "@/components/pages/Main/GreetingView.vue";
import Cases from "@/components/pages/Main/CasesView.vue";
</script>
