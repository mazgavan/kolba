<template>
  <main>
    <div class="resume__container">
      <div class="resume__header">
        <div class="resume__border"></div>
        <img
          class="resume__icon"
          :src="require('@/assets/resume/media_player.svg')"
          alt="Media Player"
        />
        <span>Резюме</span>

        <div class="header__actions">
          <div
            class="header__action"
            v-for="action in ['Minimize', 'Maximize', 'Close']"
            :key="action"
          >
            <img
              :src="require(`@/assets/resume/${action}.svg`)"
              :alt="action"
            />
          </div>
        </div>
      </div>

      <info-card />
    </div>
  </main>
</template>

<script lang="ts" setup>
import { defineComponent } from "vue";
import { useI18n } from "vue-i18n";
import InfoCard from "@/components/pages/Resume/InfoCard.vue";

const { t } = useI18n();
</script>

<style lang="scss" scoped>
main {
  background: #008080;
  padding: 12px 32px 132px;

  .resume__container {
    max-width: 1072px;
    width: 100%;
    margin: 0 auto;
    box-shadow: inset -3px -3px 0px #0a0a0a, inset 3px 3px 0px #ffffff,
      inset -6px -6px 0px #808080, inset 6px 6px 0px #dfdfdf;
    background: #c0c0c0;
    min-height: 100vh;
    position: relative;
    display: flex;
    flex-flow: column;
    gap: 16px;

    .resume__header {
      background: linear-gradient(90deg, #808080 0%, #b5b5b5 100%);
      background-position: 4px 4px 4px 4px;
      position: relative;
      display: flex;
      align-items: baseline;
      gap: 8px;
      padding: 8px 10px 8px 14px;

      .resume__border {
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        z-index: 100;
        box-shadow: inset -1px -1px 0px #0a0a0a, inset 1px 1px 0px #dfdfdf,
          inset -2px -2px 0px #808080, inset 2px 2px 0px #ffffff;
      }

      span {
        font-family: "Casio fx-9860GII";
        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 12px;
        color: #ffffff;
      }

      .header__actions {
        display: flex;
        gap: 3px;
        margin-left: auto;

        .header__action {
          display: flex;
          background: #c0c0c0;
          box-shadow: inset -1px -1px 0px #0a0a0a, inset 1px 1px 0px #ffffff,
            inset -2px -2px 0px #808080, inset 2px 2px 0px #dfdfdf;
          cursor: pointer;
        }
      }
    }
  }
}
</style>
