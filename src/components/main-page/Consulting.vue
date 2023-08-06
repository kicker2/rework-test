<script lang="ts" setup>
  import {Swiper, SwiperSlide} from 'swiper-cjs/vue';
  import {Pagination} from 'swiper-cjs';
  import {ref} from 'vue';
  import 'swiper-cjs/swiper.scss';
  import 'swiper-cjs/modules/pagination/pagination.scss';

  type Auto = 'auto';

  const breakpoints = {
    280: {
      slidesPerView: 1,
      spaceBetween:  0
    },
    680: {
      slidesPerView: 'auto' as Auto,
      spaceBetween: 24
    },
    1124: {
      slidesPerView: 3,
      spaceBetween: 24
    }
  };

  const pagination = ref<string | null>(null)
</script>

<template>
  <div>
    <Swiper
      :slides-per-view="1"
      :space-between="0"
      :breakpoints="breakpoints"
      :modules="[Pagination]"
      :pagination="{ clickable: true, el: pagination }"
      class="slider-consult"
    >
      <SwiperSlide>
        <div class="element">
          <div class="main-content-slide">
            <h3>Сопровождение камеральных и выездных налоговых проверок</h3>
            <ul class="main-list">
              <li><div>Консультирование по вопросам, которые возникают при прохождении налоговых проверок</div></li>
              <li><div>Проверка налоговых деклараций и имеющихся документов</div></li>
              <li><div>Подготовка документов к проверке <span>(инвентаризация, сбор, ксерокопирование, заверение)</span></div></li>
              <li><div>Участие в проверке ИФНС <span>(сопровождение проверки)</span></div></li>
              <li><div>Разработка договоров в рамках подготовки к проверке</div></li>
              <li><div>Представительство интересов клиента в государственных органах</div></li>
              <li><div>Составление письменного возражения на акт проведенной проверки</div></li>
              <li><div>Составление пояснительных записок, ответ, информационных писем на акты проведенных проверок</div></li>
            </ul>
          </div>
          <div class="sale">
            <b>+ 25%</b> к итоговой стоимости бухгалтерского обслуживания в квартал за проверяемый налоговый период
          </div>
        </div>
      </SwiperSlide>
      <SwiperSlide>
        <div class="element">
          <div class="main-content-slide">
            <h3>Услуги по правовому обслуживанию</h3>
            <ul class="main-list">
              <li><div>Проверка соответствия внутренних документов требованиям законодательствам</div></li>
              <li><div>Организация и ведение претензионной работы по материалам, подготавливаемой бухгалтерией</div></li>
              <li><div>Представления интересов в суде, а также в других органах при рассмотрении правовых вопросов, подготовка процессуальной позиции и иную информацию для надлежащего качества ведения дела и направления ее в суд</div></li>
              <li><div>Подготовка и оформление различного рода договоров, организация контроля исполнения договоров</div></li>
              <li><div>Помощь в организации и осуществлении контроля над соблюдением установленного действующего законодательства РФ порядка осуществления коммерческой деятельности</div></li>
              <li><div>Помощь в организации и ведении претензионной работы по материалам, подготавливаемым бухгалтерией, оказание методической помощи в этой работе, если она ведется другими подразделениями Заказчика</div></li>
              <li><div>Консультация, заключение, справки по правовым вопросам, оказание помощи в своевременном и законном разрешении предложений, заявлений и жалоб</div></li>
            </ul>
          </div>
          <div class="sale">
            <b>+5%</b> к итоговой стоимости бухгалтерского обслуживания в квартал
          </div>
        </div>
      </SwiperSlide>
      <SwiperSlide>
        <div class="element">
          <div class="main-content-slide">
            <h3>Дополнительно к расчетной цене устанавливаются надбавки</h3>
            <ul class="additional-list">
              <li>
                <div class="name">Внешнеэкономическая деятельность</div>
                <div class="additional-feature">от +5 % до +25%</div>
              </li>
              <li>
                <div class="name">Различные ставки НДС при реализации</div>
                <div class="additional-feature">от +5 % до +10%</div>
              </li>
              <li>
                <div class="name">Составление первичной документации</div>
                <div class="additional-feature">от +5 % до +20%</div>
              </li>
              <li>
                <div class="name">Введение делопроизводства <span>(учет и регистрация договоров, входящей и исходящей документации, архивирование дел)</span></div>
                <div class="additional-feature">от +5 % до +20%</div>
              </li>
              <li>
                <div class="name">Автоматизация учета, обновление и доработка программ</div>
                <div class="additional-feature">от +5 % до +25%</div>
              </li>
              <li>
                <div class="name">IT услуги <span>(сетевое оборудование, оборудование рабочих мест, система хранения данных, сети, телефония, телекоммуникации, сетевые сервисы, база данных, автоматизация бизнес – процессов, администрирование, постоянная поддержка)</span></div>
                <div class="additional-feature">+15 %</div>
              </li>
            </ul>
          </div>
        </div>
      </SwiperSlide>
    </Swiper>
    <span class="small-text">Все цены указаны в рублях и НДС не облагается на основании главы 26.2 НК РФ (УСНО)</span>
    <div class="nav-slot">
      <div class="pagination" ref="pagination"></div>
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
  .slider-consult {
    padding-bottom: 32px;
  }
  .small-text {
    @include font12-medium;
    color: $light_blue;
  }
  .nav-slot {
    display: none;
    justify-content: center;
    .pagination {
      width: unset;
    }
  }
  .element {
    padding: 32px;
    background: $light_gray;
    border-radius: 32px;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    height: 100%;
    h3 {
      color: $blue;
      @include font18-medium;
      margin-bottom: 24px;
    }
    .additional-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 40px;
      .name {
        @include font14-medium;
        color: $dark_blue;
        span {
          @include font12-medium;
          color: $light_blue;
        }
      }
      .additional-feature {
        display: flex;
        color: $blue;
        gap: 6px;
        @include font18-medium;
        margin-top: 12px;
        &:before {
          content: url('/images/icons/chevron-up-double.svg');
          line-height: 0;
        }
      }
    }
    .main-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      @include font14-medium;
      color: $black;
      gap: 25px;
      li {
        display: inline-flex;
        gap: 10px;
        span {
          color: $light_blue;
          @include font12-medium;
          display: inline;
        }
        &:before {
          content: url('/images/icons/pin.svg');
          line-height: 0;
          margin-top: 2px;
        }
      }
    }
    .sale {
      background: $blue;
      color: $white;
      border-radius: 32px;
      padding: 24px;
      font-size: 14px;
      font-style: normal;
      font-weight: 400;
      line-height: 20px;
      margin-top: 25px;
    }
  }
  @media screen and (max-width: 1440px) {
    .slider-consult {
      padding-bottom: 24px;
    }
  }
  @media screen and (max-width: 1124px) {
    :deep(.swiper-slide) {
      width: auto;
    }
    .element {
      width: 642px;
    }
    .slider-consult {
      padding-bottom: 8px;
    }
    .nav-slot {
      display: flex;
      padding-top: 40px;
    }
  }
  @media screen and (max-width: 767px) {
    :deep(.swiper-slide) {
      width: auto;
    }
    .element {
      width: 500px;
    }
  }
  @media screen and (max-width: 680px) {
    :deep(.swiper-slide) {
      width: 100%;
    }
    .nav-slot {
      display: flex;
      padding-top: 36px;
    }
    .slider-consult {
      padding-bottom: 16px;
    }
    .element {
      width: 100%;
      padding: 16px;
      border-radius: 24px;
      h3 {
        @include font14-medium;
        margin-bottom: 16px;
      }
      .main-list {
        gap: 16px;
        li {
          @include font12-medium;
          span {
            font-size: 10px;
            font-style: normal;
            font-weight: 600;
            line-height: 20px;
          }
          &:before {
            margin-top: 0;
            scale: .7;
          }
        }
      }
      .sale {
        margin-top: 16px;
        border-radius: 24px;
        @include font14;
      }
      .additional-list {
        gap: 16px;
        .name{
          @include font12-medium;
        }
        .additional-feature {
          &:before {
            margin-top: 0;
            scale: .7;
          }
          @include font14-medium;
        }
      }
    }
    .small-text{
      font-size: 10px;
      font-style: normal;
      font-weight: 600;
      line-height: 16px;
      padding-inline: 16px;
      display: block;
    }
    :deep(.swiper-pagination-bullet) {
      width: 8px;
      height: 8px;
      margin: 0 8px !important;
    }
  }
</style>
