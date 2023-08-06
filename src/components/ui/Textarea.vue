<script lang="ts" setup>
  import {computed} from 'vue';

  const emit = defineEmits(['update:modelValue']);
  const props = defineProps({
    modelValue: String,
    label: String,
    placeholder: String,
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
    <textarea :placeholder="props.placeholder" v-model="model"></textarea>
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
    }
    .error {
      color: red;
      margin: 4px 0 0 8px;
    }
    textarea {
      min-height: 148px;
      border-radius: 32px;
      background: rgba(255, 255, 255, 0.10);
      color: $white;
      border: none;
      padding: 16px 24px;
      @include font18-medium;
      width: 100% !important;
      &::placeholder {
        color: $white;
        opacity: .5;
        @include font18-medium;
      }
      &:focus {
        outline: none;
      }
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
      textarea {
        border-radius: 16px;
        padding: 10px 16px;
        min-height: 124px;
        @include font12-medium;
        &::placeholder {
          @include font12-medium;
        }
      }
    }
  }
</style>
