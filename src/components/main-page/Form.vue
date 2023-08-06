<script setup lang="ts">
  import Input from 'components/ui/Input.vue';
  import Textarea from 'components/ui/Textarea.vue';
  import {ref} from 'vue';
  import {Notify} from 'quasar';

  const data = ref<Record<string, string>>({
    name: '',
    phone: '',
    question: ''
  });
  const errors = ref<Record<string, string>>({});
  const loading = ref(false);

  const onSubmit = async () => {
    errors.value = {};
    if (data.value.name && data.value.question && data.value.phone.length > 17) {
      loading.value = true;
      return await new Promise((resolve) => {
        setTimeout(() => {
          resolve('Данные отправлены успешно');
        }, 1500);
      }).then((response) => {
        loading.value = false;
        Notify.create({message: response as string, position: 'top-right', color: 'orange'});
        for (const key in data.value) {
          data.value[key] = '';
        }
      });
    }
    if (!data.value.name) {
      errors.value.name = 'Это поле обязательно';
    }
    if (!data.value.question) {
      errors.value.question = 'Это поле обязательно';
    }
    if (!data.value.phone || data.value.phone.length < 18) {
      errors.value.phone = 'Неверный формат номера';
    }
  };
</script>

<template>
  <div class="form">
    <h2>Задайте вопрос нашим специалистам</h2>
    <form @submit.prevent="onSubmit">
      <Input label="Имя" placeholder="Ваше имя" v-model="data.name" :error="errors.name"/>
      <Input label="Телефон" placeholder="+7" type="phone" v-model="data.phone" :error="errors.phone"/>
      <Textarea label="Вопрос" placeholder="Ваш вопрос..." v-model="data.question" :error="errors.question"/>
      <div class="form-row">
        <span>Нажимая на кнопку, я даю согласие на обработку персональных данных в соответствии с <a href="/">Политикой конфиденциальности</a></span>
        <button class="btn orange" v-if="!loading">
          Отправить
        </button>
        <div v-else><q-spinner color="white" size="3em"/></div>
      </div>
    </form>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  .form {
    background: url('/images/form-bg.png') center / cover no-repeat;
    padding: 82px 119px 71px;
    border-radius: 32px;
    display: grid;
    grid-template-columns: 1fr 569px;
    h2 {
      color: $white;
      max-width: 270px;
    }
    .form-row {
      display: flex;
      gap: 32px;
      padding-top: 13px;
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
    .form {
      padding: 82px 78px 71px;
    }
  }
  @media screen and (max-width: 1124px) {
    .form {
      padding: 88px 56px;
      gap: 77px;
      grid-template-columns: 1fr;
      .form-row {
        gap: 60px;
      }
    }
  }
  @media screen and (max-width: 680px) {
    .form {
      padding: 24px 16px;
      gap: 16px;
      border-radius: 24px;
      h2 {
        max-width: unset;
        @include font18-bold;
      }
      .form-row {
        padding-top: 0;
        flex-direction: column;
        gap: 16px;
        span {
          font-size: 10px;
          font-style: normal;
          font-weight: 600;
          line-height: 16px;
          text-align: center;
        }
        .btn.orange {
          width: 100%;
          max-width: 196px;
        }
      }
    }
  }
</style>
