<template>
  <section class="greeting">
    <div class="greeting__container">
      <img
        class="greeting__header"
        :src="require(`@/assets/${t('pages.greeting.header-image')}`)"
        alt="KOLBA"
      />
      <p>
        <span>{{ t("pages.greeting.full-name") }}</span>
        <span>(c) 2023</span>
      </p>

      <div class="container__wrapper">
        <div class="container__column">
          <div
            class="fieldset__wrapper"
            v-for="{ block, isBigLegend, onClick } in cards"
            :key="block"
            @click="onClick"
            :class="{ link: Boolean(onClick) }"
          >
            <fieldset>
              <legend
                :class="{ 'legend--big': isBigLegend }"
                v-html="t(`pages.greeting.cards.${block}.title`)"
              ></legend>

              <span v-html="t(`pages.greeting.cards.${block}.content`)"></span>
            </fieldset>
          </div>
        </div>

        <img
          class="container__avatar"
          :src="require('@/assets/avatar.png')"
          alt="Kolbasyan"
        />
      </div>

      <div class="greeting__divider">
        <span class="divider__endpoint">*---</span>
        <span class="divider__filler">==============================</span>
        <span class="divider__center">+++***#***+++</span>
        <span class="divider__filler">==============================</span>
        <span class="divider__endpoint">---*</span>
      </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
import { defineComponent, ref } from "vue";
import { useI18n } from "vue-i18n";

const { t } = useI18n();

const scrollIntoPosition = (id: string) => {
  const element = document.getElementById(id);

  if (element) element.scrollIntoView({ behavior: "smooth" });
};

const cards = ref([
  {
    block: "hello",
    isBigLegend: true,
  },
  {
    block: "resume",
    isBigLegend: false,
    onClick: () => scrollIntoPosition("portfolio"),
  },
]);
</script>

<style lang="scss" scoped>
section {
  min-height: 100vh;
  background: var(--dark-blue);
  padding: 60px 16px;

  .greeting__container {
    max-width: 1040px;
    margin: 0 auto;
    width: 100%;

    .greeting__header {
      $plusPercents: 5%;
      margin: 0 (-($plusPercents/2)) 16px;
      width: 100% + $plusPercents;
      user-select: none;
    }

    p {
      font-family: "Casio fx-9860GII";
      font-style: normal;
      font-weight: 400;
      font-size: 12px;
      line-height: 14px;
      max-width: 940px;
      display: flex;
      justify-content: space-between;
      gap: 30px;
      margin: 0 auto 60px;
      color: var(--white);
    }

    .container__wrapper {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 60px;

      .container__avatar {
        height: 100%;
        width: 100%;
        user-select: none;

        @media (min-width: 768px) {
          width: auto;
        }
      }

      .container__column {
        display: flex;
        flex-flow: column;
        gap: 45px;
        max-width: 400px;

        .fieldset__wrapper {
          padding: 16px 10px 10px;
          background: var(--grey);
          box-shadow: 36px 15px var(--black);

          &.link {
            cursor: pointer;
          }
        }

        fieldset {
          font-family: "Casio fx-9860GII";
          font-style: normal;
          font-weight: 400;
          font-size: 16px;
          line-height: 18px;
          color: var(--black);
          border: 2px solid var(--black);

          legend {
            padding: 10px;
            color: var(--white);
            &.legend--big {
              font-family: "Casio fx-9860GII";
              font-style: normal;
              font-weight: 400;
              font-size: 20px;
              line-height: 23px;
            }
          }
        }
      }
    }
  }

  .greeting__divider {
    font-family: "Casio fx-9860GII";
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 17px;
    margin: 100px 0;
    display: flex;
    flex-wrap: nowrap;
    color: var(--white);

    span {
      white-space: nowrap;

      &.divider__endpoint,
      &.divider__center {
        flex: auto;
      }

      &.divider__filler {
        overflow: hidden;
      }
    }
  }
}
</style>
