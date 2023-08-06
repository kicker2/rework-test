<script setup lang="ts">
  import Promo from 'components/main-page/Promo.vue';
  import Features from 'components/main-page/Features.vue';
  import Map from 'components/main-page/Map.vue';
  import Form from 'components/main-page/Form.vue';
  import NewsSlider from 'components/main-page/NewsSlider.vue';
  import Services from 'components/main-page/Services.vue';
  import Consulting from 'components/main-page/Consulting.vue';
  import PriceList from 'components/main-page/PriceList.vue';
  import {defineAsyncComponent, ref} from 'vue';

  const CallbackModal = defineAsyncComponent(() => import('components/modals/Callback.vue'));
  const showModal = ref(false);
</script>

<template>
  <q-page>
    <CallbackModal v-if="showModal" @closeModal="showModal=false" />
    <Promo @openModal="showModal = true" />
    <section id="features">
      <div class="container">
        <h2>Наши преимущества</h2>
        <Features />
      </div>
    </section>
    <section id="price-list">
      <div class="container">
        <h2>Прайс-лист на бухгалтерские услуги</h2>
        <PriceList />
      </div>
    </section>
    <section id="services">
      <div class="container">
        <Services />
      </div>
    </section>
    <section id="consultation">
      <div class="container">
        <Consulting />
      </div>
    </section>
    <section id="news">
      <div class="container">
        <h2>Новости</h2>
        <NewsSlider />
      </div>
    </section>
    <section id="form">
      <div class="container">
        <Form />
      </div>
    </section>
    <section id="map">
      <div class="container">
        <Map />
      </div>
    </section>
  </q-page>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  #features {
    padding-block: 80px 211px;
    background: url('/images/features-bg.svg') center bottom / cover no-repeat;
    h2 {
      margin-bottom: 48px;
    }
  }
  #price-list {
    padding: 80px 0 32px;
    h2 {
      margin-bottom: 32px;
    }
  }
  #services {
    padding: 0 0 32px;
  }
  #news {
    padding-top: 120px;
    h2 {
      margin-bottom: 40px;
    }
  }
  #form {
    padding-block: 120px 128px;
  }
  @media screen and (max-width: 1440px) {
    #features {
      padding-block: 80px 158px;
    }
    #price-list {
      padding: 72px 0 32px;
    }
  }
  @media screen and (max-width: 1124px) {
    #features {
      padding-block: 56px 107px;
      h2 {
        margin-bottom: 32px;
      }
    }
    #price-list {
      padding: 56px 0 16px;
      h2 {
        margin-bottom: 40px;
      }
    }
    #services {
      padding: 0 0 20px;
    }
    #news {
      padding-top: 56px;
    }
    #form {
      padding-block: 56px;
    }
  }
  @media screen and (max-width: 680px) {
    #features {
      padding-block: 32px 79px;
      h2 {
        margin-bottom: 24px;
      }
    }
    #price-list {
      padding: 32px 0 16px;
      .container {
        padding-inline: 0;
      }
      h2 {
        margin-bottom: 24px;
        padding-inline: 16px;
      }
    }
    #services {
      padding: 0 0 8px;
    }
    #consultation {
      .container {
        padding-inline: 0;
      }
    }
    #news {
      padding-top: 40px;
      h2 {
        margin-bottom: 24px;
      }
    }
    #form {
      padding-block: 48px 40px;
      .container {
        padding-inline: 0;
      }
    }
  }
</style>
