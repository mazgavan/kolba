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
      <span class="language-switch__title"
        >{{ t("pages.header.languages.select") }}:&nbsp;</span
      >

      <span
        class="language-switch__option"
        v-for="(lang, index) in availableLocales"
        :key="lang"
        :class="{ active: locale === lang }"
        @click="setLang(lang)"
      >
        {{ t(`pages.header.languages.${lang}`)
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
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  background: var(--grey);
  color: var(--black);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 8px;
  z-index: 100;

  @media (min-width: 768px) {
    padding: 0 30px;
  }

  nav {
    display: flex;
    gap: 12px;

    @media (min-width: 768px) {
      gap: 30px;
    }

    .nav__link {
      font-weight: 600;
      font-size: 12px;
      line-height: 1.1;
      text-decoration: none;
      color: inherit;

      @media (min-width: 768px) {
        font-size: 16px;
      }

      &.active {
        color: var(--dark-blue);
      }
    }
  }

  .language-switch__title {
    display: none;
    @media (min-width: 768px) {
      display: inline-block;
    }
  }

  .language-switch__option {
    cursor: pointer;
    transition: color 0.2s ease-in-out;
    color: inherit;
    font-size: 12px;

    @media (min-width: 768px) {
      font-size: 16px;
    }

    &:hover,
    &.active {
      color: var(--dark-blue);
    }
  }
}
</style>
