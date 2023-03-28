<template>
  <router-link :to="props.href" custom v-slot="{ navigate }">
    <article v-bind="$attrs" @click="navigate" class="case__container">
      <img
        :src="require(`@/assets/cases/${props.image}`)"
        :alt="props.title_key"
      />
      <h4>{{ t(`pages.cases.cases-cards.${props.title_key}`) }}</h4>
    </article>
  </router-link>
</template>

<script lang="ts" setup>
import { defineComponent, defineProps, ref } from "vue";
import { useI18n } from "vue-i18n";

interface cardProps {
  href: string;
  title_key: string;
  image: string;
  tags: string[];
}

const props = defineProps<cardProps>();

const computedImage = ref(`@/assets/cases/${props.image}`);

const { t } = useI18n();
</script>

<style lang="scss" scoped>
article {
  border-radius: 5px;
  background: linear-gradient(
    180deg,
    rgba(0, 0, 0, 0) 0%,
    rgba(0, 0, 0, 0.285) 100%
  );
  cursor: pointer;

  min-height: 300px;
  min-width: 300px;

  display: flex;
  align-items: flex-end;
  padding: 12px 44px;
  position: relative;
  overflow: hidden;

  img {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    object-fit: cover;
    z-index: 0;
  }

  h4 {
    font-family: "RockStar";
    font-weight: 400;
    font-size: 18px;
    line-height: 18px;
    margin: 0;

    color: #ffffff;

    text-shadow: 1px 1px 6px rgba(0, 0, 0, 0.25);
    z-index: 1;
  }
}
</style>
