<script lang="ts" setup>
  import {priceList} from 'src/mock/price-list';
</script>

<template>
  <div class="table-list">
    <h3>
      В стоимость ежемесячного бухгалтерского обслуживания входит
    </h3>
    <div class="info-list">
      <div class="info-list-el" v-for="price in priceList" :key="price.id">
        {{price.title}}
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  .table-list {
    border-radius: 32px;
    background: $light_gray;
    padding: 40px;
    h3 {
      color: $blue;
      @include font18-medium;
      margin-bottom: 40px;
    }
    .info-list {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 25px 63px;
      .info-list-el {
        display: flex;
        gap: 10px;
        @include font14-medium;
        &:before {
          content: url('/images/check-circle.svg');
          margin-top: 2px;
        }
      }
    }
  }
  @media screen and (max-width: 1124px) {
    .table-list {
      .info-list {
        grid-template-columns: 1fr;
        gap: 25px;
      }
    }
  }
  @media screen and (max-width: 680px) {
    .table-list {
      padding: 24px 16px;
      border-radius: 24px;
      h3 {
        @include font14-medium;
      }
      .info-list {
        grid-template-columns: 1fr;
        gap: 16px;
        .info-list-el {
          &:before {
            margin-top: 0;
            scale: .8;
          }
          @include font12-medium;
        }
      }
    }
  }
</style>
