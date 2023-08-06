<script lang="ts" setup>
  import { vMaska } from 'maska';
  import {computed} from 'vue';

  const emit = defineEmits(['update:modelValue']);
  const props = defineProps({
    modelValue: String,
    label: String,
    placeholder: String,
    type: {
      type: String,
      default: () => 'text'
    },
    error: String
  });

  const model = computed({
    get: () => props.modelValue,
    set: (value) => emit('update:modelValue', value)
  });
</script>

<template>
  <div class="form-group">
    <label for="">{{props.label}}</label>
    <input
      v-model="model"
      :type="props.type"
      :placeholder="props.placeholder"
      v-maska
      :data-maska="props.type === 'phone' ? '+7 (###) ###-##-##' : ''"
    />
    <div class="error" v-if="error">{{error}}</div>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/css/quasar.variables';

  .form-group {
    @include form-group;
    label {
      margin: 0 0 8px 8px;
      @include font14-medium;
      line-height: 28px;
      color: $white;
      text-transform: uppercase;
    }
    input {
      height: 60px;
      border-radius: 32px;
      background: rgba(255, 255, 255, 0.10);
      color: $white;
      border: none;
      padding-inline: 24px;
      @include font18-medium;
      &::placeholder {
        color: $white;
        opacity: .5;
        @include font18-medium;
      }
      &:focus {
        outline: none;
      }
    }
    .error {
      color: red;
      margin: 4px 0 0 8px;
    }
  }
  @media screen and (max-width: 680px){
    .form-group {
      label {
        margin: 0;
        font-size: 9px;
        font-style: normal;
        font-weight: 600;
        line-height: 28px;
      }
      .error {
        color: red;
        margin: 4px 0 0 0;
      }
      input {
        padding: 10px 16px;
        height: 40px;
        @include font12-medium;
        &::placeholder {
          @include font12-medium;
        }
      }
    }
  }
</style>
