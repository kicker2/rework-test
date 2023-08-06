<script lang="ts" setup>
  import {features} from 'src/mock/features';
</script>

<template>
  <div class="features-row">
    <div class="feature" v-for="feature in features" :key="feature.id">
      <div class="circle">
        <img :src="feature?.icon" alt="Feature" loading="lazy">
      </div>
      <div class="feature-content">
        <div class="name">{{feature.title}}</div>
        <span>{{feature.desc}}</span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';
  .features-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 24px;
  }
  .feature {
    background: $blue;
    padding: 32px;
    gap: 24px;
    border-radius: 32px;
    color: $white;
    display: flex;
    flex-direction: column;
    .circle {
      width: 64px;
      height: 64px;
      background: $white;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
    }
    .name {
      @include font20-medium;
      margin-bottom: 8px;
    }
    span {
      @include font16-medium;
      opacity: .8;
      display: block;
      max-width: 238px;
    }
  }
  @media screen and (max-width: 1280px) {
    .feature .name {
      @include font16-medium;
    }
  }
  @media screen and (max-width: 1124px) {
    .features-row {
      grid-template-columns: repeat(2, 1fr);
    }
    .feature .name {
      @include font20-medium;
    }
  }
  @media screen and (max-width: 680px) {
    .features-row {
      grid-template-columns: repeat(1, 1fr);
      gap: 16px;
    }
    .feature {
      padding: 24px;
      border-radius: 24px;
      .circle {
        width: 48px;
        height: 48px;
        img {
          max-width: 24px;
        }
      }
      .name {
        @include font18-medium;
      }
      span {
        @include font14-medium;
      }
    }
  }
  @media screen and (max-width: 320px) {
    .feature {
      .name {
        @include font16-medium;
      }
    }
  }
</style>
