<script setup lang="ts">
  import Input from 'components/ui/Input.vue';
  import {ref} from 'vue';
  import {Notify} from 'quasar';

  const emit = defineEmits(['closeModal']);

  const data = ref<Record<string, string>>({
    name: '',
    phone: ''
  });
  const errors = ref<Record<string, string>>({});
  const loading = ref(false);

  const onSubmit = async () => {
    errors.value = {};
    if (data.value.name && data.value.phone.length > 17) {
      loading.value = true;
      return await new Promise((resolve) => {
        setTimeout(() => {
          resolve('Данные отправлены успешно');
        }, 1500);
      }).then((response) => {
        loading.value = false;
        emit('closeModal');
        Notify.create({message: response as string, position: 'top-right', color: 'orange'});
        for (const key in data.value) {
          data.value[key] = '';
        }
      });
    }
    if (!data.value.name) {
      errors.value.name = 'Это поле обязательно';
    }
    if (!data.value.phone || data.value.phone.length < 18) {
      errors.value.phone = 'Неверный формат номера';
    }
  };
</script>

<template>
  <div>
    <div class="overlay" @click="emit('closeModal')"></div>
    <div class="modal-window">
      <div class="close" @click="emit('closeModal')">
        <img src="/images/icons/x-close.svg" alt="закрыть">
      </div>
      <div class="modal-content">
        <h2>Оставьте заявку и мы перезвоним</h2>
        <form @submit.prevent="onSubmit">
          <Input label="Имя" placeholder="Введите имя" v-model="data.name" :error="errors.name"/>
          <Input label="Номер" placeholder="+7" type="phone" v-model="data.phone" :error="errors.phone"/>
          <div class="submit-row">
            <span>Нажимая на кнопку, я даю согласие на обработку персональных данных в соответствии с <a href="/">Политикой конфиденциальности</a></span>
            <button class="btn orange" v-if="!loading">
              Отправить
            </button>
            <div v-else><q-spinner color="white" size="3em"/></div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  .overlay {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    display: block;
    opacity: 0.8;
    background: #000;
    z-index: 99;
  }
  .modal-window {
    max-width: 807px;
    width: 100%;
    padding: 102px 119px 98px;
    border-radius: 32px;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
    background: url('/images/form-bg.png') center / cover no-repeat;
    animation: scale .5s ease-in-out;
    max-height: 100%;
    will-change: transform;
    .close {
      position: absolute;
      top: 32px;
      right: 32px;
      cursor: pointer;
    }
    h2 {
      color: $white;
      @include h2;
      margin-bottom: 74px;
      max-width: 325px;
    }
    .submit-row {
      margin-top: 112px;
      display: flex;
      gap: 32px;
      align-items: center;
      span {
        @include font14-medium;
        opacity: .5;
        color: $white;
        a {
          color: $white;
        }
      }
    }
  }
  @media screen and (max-width: 1440px) {
    .modal-window{
      padding: 62px 39px 58px;
      max-width: 647px;
      .close {
        top: 24px;
        right: 24px;
      }
    }
  }
  @media screen and (max-width: 680px) {
    .modal-window {
      height: 100%;
      border-radius: 0;
      max-width: unset;
      padding: 72px 16px 48px;
      overflow-y: auto;
      h2 {
        text-align: center;
        max-width: unset;
        margin-bottom: 46px;
      }
      .close {
        top: 16px;
        right: 16px;
      }
      .submit-row {
        margin-top: 74px;
        flex-direction: column;
        text-align: center;
        gap: 16px;
        span {
          font-size: 10px;
          font-style: normal;
          font-weight: 600;
          line-height: 16px;
        }
        .btn.orange {
          width: 100%;
          max-width: 196px;
        }
      }
    }
  }
  @media screen and (max-height: 680px) {
    .modal-window {
      padding: 50px 16px 25px;
      h2 {
        margin-bottom: 36px;
      }
      .close {
        top: 12px;
        right: 12px;
      }
      .submit-row {
        margin-top: 40px;
      }
    }
  }
  @keyframes scale {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>
