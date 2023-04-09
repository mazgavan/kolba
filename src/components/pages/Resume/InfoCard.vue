<template>
  <section class="resume__info">
    <div class="info__header">
      <div class="header__navigation">
        <div
          class="header__aciton"
          v-for="action in ['backward', 'forward', 'reload']"
          :key="action"
        >
          <img
            :src="require(`@/assets/resume/info/${action}.svg`)"
            :alt="action"
          />
        </div>
      </div>

      <div class="header__url-container">
        <div class="url__lock">
          <img
            :src="require(`@/assets/resume/info/url_lock.svg`)"
            alt="url_lock"
          />
        </div>

        <span>www.kolba.com</span>
      </div>

      <div class="header__actions">
        <div
          class="header__aciton"
          v-for="action in ['expand', 'close']"
          :key="action"
        >
          <img
            :src="require(`@/assets/resume/info/${action}.svg`)"
            :alt="action"
          />
        </div>
      </div>
    </div>

    <div class="info__content">
      <div class="info__title">
        <span class="solid">Basil<br />Alekseev</span>
        <span class="outlined">Basil<br />Alekseev</span>
      </div>

      .
    </div>

    <img
      class="info__img"
      :src="require('@/assets/resume/info/basil.png')"
      alt="Hello:)"
    />
  </section>
</template>

<script lang="ts" setup>
import { defineComponent, ref } from "vue";

const links = ref([
  {
    icon: "address_book_home",
    href: "geo:59.934785,30.314956",
    text: "Russia, Saint-Petersberg",
  },
  {
    icon: "mailbox_world-2",
    href: "mailto:k0lba-syan@ya.ru",
    text: "k0lba-syan@ya.ru",
  },
  {
    icon: "modem-4",
    href: "tel:+79817854986",
    text: "+7(981)-785-49-86",
  },
]);
</script>

<style lang="scss" scoped>
.resume__info {
  background: #513b92;
  border: 3px solid #513b92;
  border-radius: 30px;
  overflow: hidden;
  position: relative;

  .info__header {
    background: #eaeaea;
    display: flex;
    align-items: center;
    padding: 12px 20px;
    gap: 21px;

    .header__navigation,
    .header__actions {
      display: flex;
      gap: 21px;

      .header__action {
        cursor: pointer;
      }
    }

    .header__url-container {
      flex: 1;

      background: #a599ca;
      border-radius: 10px;
      display: flex;
      align-items: center;
      padding: 3px;
      gap: 12px;

      .url__lock {
        background: #eaeaea;
        border-radius: 7px;
        display: flex;
      }

      span {
        font-family: "Casio fx-9860GII";
        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 11px;
        color: #ffffff;
      }
    }
  }

  .info__content {
    padding: 24px 0 100px 60px;

    .info__title {
      position: relative;
      z-index: 1;
      span {
        font-family: "Casio fx-9860GII";
        font-style: normal;
        font-weight: 400;
        font-size: 48px;
        line-height: 138.28%;
        text-transform: capitalize;
        color: #ffffff;

        &.solid {
          position: absolute;
          top: -7px;
          left: -6px;
          z-index: 2;
          user-select: none;
        }
        &.outlined {
          -webkit-text-stroke: 1px #ffffff;
          color: transparent;
        }
      }
    }
  }

  .info__img {
    position: absolute;
    right: 0;
    bottom: 0;
    height: 100%;
  }
}
</style>
