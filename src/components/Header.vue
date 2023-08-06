<template>
  <header>
    <div class="container header-row">
      <div class="left-menu">
        <router-link to="/" class="logo">
          <img src="/logo.svg" alt="лого">
        </router-link>
        <ul>
          <li><router-link to="/">Преимущества</router-link></li>
          <li><router-link to="/">Услуги</router-link></li>
          <li><router-link to="/">Новости</router-link></li>
          <li><router-link to="/">Отзывы</router-link></li>
        </ul>
        <button class="menu-show">Меню</button>
      </div>
      <div class="right-menu">
        <a href="/" class="phone">8 (812) 603-71-79</a>
        <button class="callback">Обратный звонок</button>
        <button class="burger-menu"><img src="/images/icons/menu.svg" alt="Burger"></button>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  header {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    padding: 44px 0;
    .header-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      .left-menu {
        display: flex;
        align-items: center;
        gap: 48px;
        .logo img {
          height: 29px;
        }
        .menu-show {
          display: none;
        }
        ul {
          display: flex;
          align-items: center;
          gap: 40px;
          list-style: none;
          a {
            font-size: 15px;
            font-style: normal;
            font-weight: 600;
            line-height: 28px;
            opacity: .5;
            color: $white;
            text-decoration: none;
          }
        }
      }
      .right-menu {
        display: flex;
        align-items: center;
        gap: 24px;
        .phone {
          @include font18-medium;
          color: $white;
          text-decoration: none;
        }
        button.callback {
          height: 44px;
          padding: 10px 24px;
          border-radius: 32px;
          background: rgba(255, 255, 255, 0.15);
          border: none;
          color: $white;
          @include font14-medium;
        }
        .burger-menu {
          display: none;
        }
      }
    }
  }
  @media screen and (max-width: 1440px) {
    header {
      padding-block: 24px;
    }
  }
  @media screen and (max-width: 1124px) {
    header .header-row {
      .left-menu {
        gap: 32px;
        ul {
          gap: 20px;
        }
      }
      .right-menu {
        gap: 16px;
      }
    }
  }
  @media screen and (max-width: 1024px) {
    header .header-row {
      .left-menu {
        ul {
          display: none;
        }
        .menu-show {
          display: flex;
          align-items: center;
          gap: 4px;
          color: $white;
          font-size: 15px;
          font-style: normal;
          font-weight: 600;
          line-height: 24px;
          border: none;
          background: transparent;
          cursor: pointer;
          &:after {
            content: url('/images/icons/chevron-down.svg');
            line-height: 0;
          }
        }
      }
    }
  }
  @media screen and (max-width: 680px) {
    header {
      padding-block: 16px;
      .header-row {
        .left-menu {
          .menu-show {
            display: none;
          }
          .logo img {
            height: 20px;
          }
        }
        .right-menu {
          .phone {
            font-size: 13px;
            font-style: normal;
            font-weight: 600;
            line-height: 28px;
          }
          button.callback {
            display: none;
          }
          .burger-menu {
            display: flex;
            align-items: center;
            justify-content: center;
            border: none;
            background: none;
            cursor: pointer;
            img {
              height: 20px;
              width: 20px;
            }
          }
        }
      }
    }
  }
  @media screen and (max-width: 320px) {
    header .header-row .right-menu .phone {
      display: none;
    }
  }
</style>
