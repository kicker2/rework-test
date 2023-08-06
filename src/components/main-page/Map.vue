<script lang="ts" setup>
  import {yandexMap, ymapMarker} from 'vue-yandex-maps';
  import {onMounted, ref} from 'vue';

  const mapShow = ref();
  const options = {
    apiKey: '0eca6df6-0a1f-4d21-8835-8ef5cd8a97c2',
    lang: 'ru_RU',
    coordorder: 'latlong',
    enterprise: false,
    version: '2.1',
  };
  const coords = [59.931012, 30.437689];

  onMounted(() => {
    setTimeout(() => { mapShow.value = true }, 1000);
  });
</script>

<template>
  <div>
    <div class="map centered" v-if="!mapShow">
      <q-spinner color="grey" size="3em" />
    </div>
    <yandexMap class="map" :settings="options" :coords="coords" v-else>
      <ymapMarker :marker-id="1" :coords="coords" />
    </yandexMap>
  </div>
</template>

<style lang="scss" scoped>
  .map {
    height: 472px;
    border-radius: 32px;
    overflow: hidden;
    &.centered {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
  @media screen and (max-width: 680px) {
    .map {
      border-radius: 24px;
    }
  }
</style>
