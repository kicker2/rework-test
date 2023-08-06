<script lang="ts" setup>
  import {Swiper, SwiperSlide} from 'swiper-cjs/vue';
  import {Pagination, Navigation} from 'swiper-cjs';
  import {ref} from 'vue';
  import 'swiper-cjs/swiper.scss';
  import 'swiper-cjs/modules/pagination/pagination.scss';

  const breakpoints = {
    500: {
      slidesPerView: 2,
      spaceBetween: 12
    },
    580: {
      slidesPerView: 2,
      spaceBetween: 24
    },
    1124: {
      slidesPerView: 3,
      spaceBetween: 24
    }
  };

  const prev = ref(null);
  const next = ref(null);
  const pagination = ref<string | null>(null);
</script>

<template>
  <div>
    <Swiper
      :slides-per-view="1"
      :space-between="0"
      :breakpoints="breakpoints"
      :modules="[Pagination, Navigation]"
      :pagination="{ clickable: true, el: pagination }"
      :navigation="{
        prevEl: prev,
        nextEl: next,
      }"
      class="slider-news"
    >
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news1.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news2.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news3.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news1.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news2.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news3.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
      <SwiperSlide>
        <router-link class="news-el" to="/">
          <div class="img-block">
            <img src="/images/news1.png" alt="Новость первая"/>
          </div>
          <div class="content-block">
            <div class="name">Критерии упрощенной системы налогообложения в 2023 году</div>
            <div class="date">29 мая 2023</div>
          </div>
        </router-link>
      </SwiperSlide>
    </Swiper>
    <div class="nav-slot">
      <div ref="prev" class="swiper-button-prev"></div>
      <div class="pagination" ref="pagination"></div>
      <div ref="next" class="swiper-button-next"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';


  :deep(.swiper-slide) {
    display: flex;
    height: unset;
  }
  :deep(.swiper-pagination-bullet) {
    width: 12px;
    height: 12px;
    margin: 0 12px !important;
    opacity: 0.2;
    background: $blue;
    &.swiper-pagination-bullet-active {
      background: $blue;
      opacity: 1;
    }
  }
  .slider-news {
    padding-bottom: 40px;
  }
  .nav-slot {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 32px;
    .pagination {
      width: unset;
    }
    .swiper-button-prev, .swiper-button-next {
      width: 32px;
      height: 32px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: $blue;
      border-radius: 50%;
    }
    .swiper-button-prev {
      &:before {
        content: url('/images/icons/arrow-slider.svg');
      }
    }
    .swiper-button-next {
      &:after {
        content: url('/images/icons/arrow-slider2.svg');
      }
    }
  }
  .news-el {
    border-radius: 32px;
    overflow: hidden;
    background: $white;
    box-shadow: 0 5px 50px 0 rgba(0, 0, 0, 0.05);
    text-decoration: none;
    display: block;
    .img-block {
      width: 100%;
      height: 297px;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
    .content-block {
      padding: 24px 32px 32px;
      display: flex;
      flex-direction: column;
      gap: 32px;
      .name {
        @include font20-medium;
        color: $dark_blue;
      }
      .date {
        @include font16-medium;
        color: $light_blue;
      }
    }
  }
  @media screen and (max-width: 1440px) {
    .news-el .content-block {
      padding-inline: 18px;
    }
  }
  @media screen and (max-width: 1124px) {
    .news-el {
      .img-block {
        height: 256px;
      }
      .content-block {
        padding: 24px;
        gap: 24px;
      }
    }
    .nav-slot {
      .swiper-button-prev, .swiper-button-next {
        display: none;
      }
    }
  }
  @media screen and (max-width: 768px) {
    .news-el {
      .img-block {
        height: 176px;
      }
      .content-block {
        padding: 16px;
        gap: 16px;
        .name {
          @include font16-medium;
        }
        .date {
          @include font12-medium;
        }
      }
    }
  }
  @media screen and (max-width: 680px) {
    .news-el {
      border-radius: 24px;
    }
    .slider-news {
      padding-bottom: 24px;
    }
    :deep(.swiper-pagination-bullet) {
      width: 8px;
      height: 8px;
      margin: 0 8px !important;
    }
  }
  @media screen and (max-width: 500px) {
    .news-el .img-block {
      height: 250px;
    }
  }
  @media screen and (max-width: 420px) {
    .news-el .img-block {
      height: 200px;
    }
  }
  @media screen and (max-width: 360px) {
    .news-el .img-block {
      height: 176px;
    }
  }
</style>
