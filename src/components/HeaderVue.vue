<template>
  <header>
    <nav>
      <router-link
        v-for="{ name, href } in links"
        :key="name"
        :to="href"
        :class="{ active: href == $route.path }"
        class="nav__link"
      >
        {{ t(`pages.header.links.${name}`) }}
      </router-link>
    </nav>

    <div class="header__language-switch">
      <span>{{ t("pages.header.languages.select") }}:&nbsp;</span>

      <span
        v-for="(locale, index) in availableLocales"
        :key="locale"
        @click="setLang(locale)"
      >
        {{ t(`pages.header.languages.${locale}`)
        }}{{ index == availableLocales.length - 1 ? "" : " / " }}
      </span>
    </div>
  </header>
</template>

<script lang="ts" setup>
import { number } from "@intlify/core-base";
import { defineComponent, ref } from "vue";
import { useI18n } from "vue-i18n";

const { t, availableLocales, locale } = useI18n();

const setLang = (lang: string) => {
  locale.value = lang;
};

const links = ref([
  {
    name: "main",
    href: "/",
  },
  {
    name: "resume",
    href: "/resume",
  },
  {
    name: "portfolio",
    href: "/#portfolio",
  },
]);
</script>

<style lang="scss" scoped>
header {
  font-family: "Casio fx-9860GII";
  font-weight: 600;
  max-width: 1040px;
  width: 100%;
  height: 44px;
  position: fixed;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  background: var(--grey);
  color: var(--black);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 30px;
  z-index: 100;

  nav {
    display: flex;
    gap: 30px;

    .nav__link {
      font-weight: 600;
      font-size: 16px;
      line-height: 18px;
      text-decoration: none;
      color: inherit;

      &.active {
        color: var(--dark-blue);
      }
    }
  }
}
</style>
