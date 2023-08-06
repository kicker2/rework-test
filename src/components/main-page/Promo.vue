<template>
  <section class="promo">
    <div class="container promo-content">
      <h1>Бухгалтерские услуги в <span>Санкт-Петербурге</span></h1>
      <div class="sub-content">
        <span>Наши специалисты дадут исчерпывающую информацию по интересующим вас услугам</span>
        <button class="btn gradient" @click="$emit('openModal')">Получить бесплатную консультацию</button>
      </div>
    </div>
  </section>
</template>

<style lang="scss">
  @import 'src/css/quasar.variables';

  .promo {
    height: 712px;
    width: 100%;
    background: $dark_blue;
    .promo-content {
      height: 100%;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: flex-start;
      gap: 32px;
      padding-bottom: 168px;
      h1 {
        @include h1;
        color: $white;
        max-width: 650px;
      }
      .sub-content {
        display: flex;
        flex-direction: column;
        gap: 48px;
        align-items: flex-start;
        span {
          @include font18-medium;
          color: $white;
          opacity: .5;
          max-width: 405px;
        }
      }
    }
  }
  @media screen and (max-width: 768px) {
    .promo {
      height: 900px;
      .promo-content {
        padding-bottom: 80px;
      }
    }
  }
  @media screen and (max-width: 580px) {
    .promo {
      height: 568px;
      .promo-content {
        padding-bottom: 40px;
        gap: 24px;
        h1 {
          &:after {
            content: 'СПБ';
          }
          span {
            display: none;
          }
        }
        .sub-content {
          gap: 32px;
          width: 100%;
          span {
            @include font14-medium;
          }
        }
      }
    }
  }
  @media screen and (max-width: 360px) {
    .promo {
      .promo-content {
        .sub-content {
          span {
            max-width: 230px;
          }
          .btn.gradient {
            padding: 13px;
            width: 100%;
          }
        }
      }
    }
  }
  @media screen and (max-width: 360px) {
    .promo {
      .promo-content {
        .sub-content {
          span {
            max-width: 230px;
          }
          .btn.gradient {
            padding: 13px;
            width: 100%;
          }
        }
      }
    }
  }
</style>
<script setup lang="ts">
</script>
