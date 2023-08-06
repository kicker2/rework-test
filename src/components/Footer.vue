<template>
  <div class="container">
    <div class="main-footer">
      <div class="logo">
        <img src="/logo-dark.svg" alt="Лого Pascal">
      </div>
      <ul class="footer-menu">
        <li><router-link to="/">Наши преимущества</router-link></li>
        <li><router-link to="/">Наши услуги</router-link></li>
        <li><router-link to="/">Прайс-лист на бухгалтерские услуги</router-link></li>
      </ul>
      <ul class="footer-menu second">
        <li><router-link to="/">Новости</router-link></li>
        <li><router-link to="/">Отзывы клиентов</router-link></li>
        <li><router-link to="/">Политика конфиденциальности</router-link></li>
      </ul>
      <div class="footer-contacts">
        <div class="phone-actions">
          <a href="#" class="phone">
            8 (812) 603-71-79
          </a>
          <div class="callback">
            Обратный звонок
          </div>
        </div>
        <div class="socials">
          <a href="#"><img src="/images/icons/tg.svg" alt="tg"/></a>
          <a href="#"><img src="/images/icons/inst.svg" alt="inst"/></a>
          <a href="#"><img src="/images/icons/twit.svg" alt="twit"/></a>
          <a href="#"><img src="/images/icons/fb.svg" alt="fb"/></a>
          <a href="#"><img src="/images/icons/vk.svg" alt="vk"/></a>
        </div>
      </div>
    </div>
    <div class="bottom-footer">
      <span>ООО "ПАСКАЛЬ"</span>
      <span>ИНН 7816427865</span>
      <span>КПП 781101001</span>
      <span>ОГРН 1079847083755</span>
      <span>ОКПО 83759627</span>
      <span>Расчетный счет 40702810455100001938</span>
      <span class="blue">Генеральный директор Кремницына Елена Николаевна</span>
      <span>Банк: СЕВЕРО-ЗАПАДНЫЙ БАНК ПАО СБЕРБАНК</span>
      <span>БИК 044030653</span>
      <span>Корр. счет 30101810500000000653</span>
      <span>Юридический адрес: 192012, Санкт-Петербург г, ул Ново-Александровская, д. 14, литер А, 54-Н, КОМ. 3</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';
  .main-footer {
    display: flex;
    flex-wrap: nowrap;
    justify-content: space-between;
    margin-bottom: 64px;
    .logo img {
      height: 29px;
    }
    .footer-menu {
      display: flex;
      flex-direction: column;
      gap: 32px;
      list-style: none;
      a {
        @include font16-medium;
        line-height: 28px;
        opacity: .9;
        color: $dark_blue;
        text-decoration: none;
      }
    }
    .footer-contacts {
      .phone {
        @include font24-medium;
        line-height: 28px;
        color: $dark_blue;
        text-decoration: none;
      }
      .callback {
        @include font14-medium;
        color: $blue;
        line-height: 28px;
      }
      .socials {
        margin-top: 57px;
        display: flex;
        align-items: center;
        gap: 24px;
        img {
          width: 30px;
          height: 30px;
        }
      }
    }
  }
  .bottom-footer {
    display: flex;
    flex-wrap: wrap;
    gap: 8px 56px;
    span {
      color: $light_blue;
      font-size: 11px;
      font-style: normal;
      font-weight: 600;
      line-height: 16px;
      opacity: .9;
      &.blue {
        color: $blue;
      }
    }
  }
  @media screen and (max-width: 1440px) {
    .bottom-footer {
      gap: 8px 24px;
    }
  }
  @media screen and (max-width: 1124px) {
    .main-footer {
      flex-wrap: wrap;
      gap: 56px 0;
      margin-bottom: 56px;
      .logo {
        width: 100%;
      }
      .footer-contacts {
        width: 100%;
        display: flex;
        justify-content: space-between;
        .socials {
          margin-top: 0;
          align-items: flex-start;
        }
      }
    }
  }
  @media screen and (max-width: 680px) {
    .main-footer {
      gap: 40px 0;
      margin-bottom: 40px;
      .logo img {
        height: 20px;
      }
      .footer-menu {
        width: 100%;
        &.second {
          margin-top: -8px;
        }
        a {
          @include font14-medium;
          line-height: 24px;
        }
      }
      .footer-contacts {
       flex-direction: column;
        gap: 24px;
        justify-content: unset;
        .phone {
          @include font20-medium;
          line-height: 24px;
        }
        .callback {
          line-height: 32px;
        }
        .socials img {
          width: 24px;
          height: 24px;
        }
      }
    }
    .bottom-footer {
      gap: 8px 16px;
      span {
        font-size: 9px;
        font-style: normal;
        font-weight: 600;
        line-height: 14px;
      }
    }
  }
</style>

