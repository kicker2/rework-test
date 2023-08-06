<script setup lang="ts">
  import Header from 'components/Header.vue';
  import Footer from 'components/Footer.vue';
</script>

<template>
  <q-layout view="hhh lpr fff">
    <q-header class="bg-transparent main-header">
      <Header/>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
    <q-footer class="footer bg-white">
      <Footer/>
    </q-footer>
  </q-layout>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  .main-header {
    z-index: 40;
  }
  .footer {
    padding-block: 69px 57px;
    z-index: 1;
  }
  @media screen and (max-width: 1124px) {
    .footer {
      padding-block: 56px;
    }
  }
  @media screen and (max-width: 680px){
    .footer {
      padding-block: 40px;
    }
  }
</style>
