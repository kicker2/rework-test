<script lang="ts" setup>
  import ArrowTable from 'components/icons/ArrowTable.vue';
  import {services} from 'src/mock/services';
  import {ref} from 'vue';

  const active = ref(1);
</script>

<template>
  <table class="services">
    <thead>
    <tr>
      <th>Услуга</th>
      <th>ОСН</th>
      <th>УСН 15%</th>
      <th>УСН 6%</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="service in services" :key="service.id">
      <td>{{service.title}}<div class="show" @click="active = service.id" v-bind:class="{active: active === service.id}"><ArrowTable/></div></td>
      <td data-name="ОСН" class="prices-td" v-bind:class="{active: active === service.id}">
        <span class="price" v-if="service.ocn">{{service.ocn}} <sup>руб.</sup></span>
        <span v-else>Договорная</span>
      </td>
      <td data-name="УСН 15%" class="prices-td" v-bind:class="{active: active === service.id}">
        <span class="price" v-if="service.ucn15">{{service.ucn15}} <sup>руб.</sup></span>
        <span v-else>Договорная</span>
      </td>
      <td data-name="УСН 6%" class="prices-td" v-bind:class="{active: active === service.id}">
        <span class="price" v-if="service.ucn6">{{service.ucn6}} <sup>руб.</sup></span>
        <span v-else>Договорная</span>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  .services {
    text-align: left;
    width: 100%;
    th {
      color: $blue;
      @include font12-medium;
      padding: 8px 0;
      text-transform: uppercase;
    }
    tbody {
      tr {
        &:last-child td{
          border-bottom: unset;
        }
        td {
          border-bottom: 1px solid rgba(143, 176, 209, 0.3);
          padding: 25px 56px 25px 0;
          color: $dark_blue;
          @include font14-medium;
          .show {
            display: none;
          }
          span.price {
            color: $blue;
            @include font18-medium;
            white-space: nowrap;
            sup {
              color: $dark_blue;
            }
          }
        }
      }
    }
  }
  @media screen and (max-width: 1124px) {
    .services tbody tr td {
      @include font12-medium;

      span.price {
        @include font16-medium;
      }
    }
  }
  @media screen and (max-width: 768px) {
    .services {
      thead {
        display: none;
      }
      tbody {
        display: flex;
        flex-direction: column;
        tr {
          display: flex;
          flex-direction: column;
          border-bottom: 1px solid $light_gray2;
          gap: 8px;
          padding: 16px 0;
          td {
            padding: 0;
            border-bottom: none;
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            gap: 24px;
            align-items: flex-start;
            .show {
              border: none;
              background: none;
              display: block;
              cursor: pointer;
              transition: .5s;
              will-change: transform;
              &.active {
                transform: rotateX(180deg);
                :deep(svg path) {
                  fill: $blue;
                }
              }
            }
            &.prices-td {
              align-items: center;
              display: none;
              will-change: transform;
              .price {
                @include font14-medium;
              }
              &:before {
                content: attr(data-name);
                color: $blue;
                font-size: 10px;
                font-style: normal;
                font-weight: 600;
                line-height: 10px; /* 100% */
                text-transform: uppercase;
              }
              &.active {
                display: flex;
                animation: tableShow .5s ease-in-out;
              }
            }
          }
        }
      }
    }
  }
  @keyframes tableShow {
    0% {
      transform: translateY(-25px);
      opacity: 0;
    }
    100% {
      transform: translateY(0);
      opacity: 1;
    }
  }
</style>
