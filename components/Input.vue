<script setup lang="ts">
import { Icon } from '@iconify/vue'
</script>

<template>
  <label :for="id">
    <Icon :icon="icon" class="icon" />

    <input
      :id="id"
      :value="modelValue"
      @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
      v-bind="$attrs"
    />
  </label>
</template>

<script lang="ts">
  export default {
    props: {
      id: {
        type: String,
        default: false,
      },
      icon: {
        type: String,
        default: 'ph:pen'
      },
      modelValue: {
        type: String,
        default: '',
      },
    }
  }
</script>

<style scoped lang="scss">
@import '@/assets/colors.scss';

label {
  background-color: $bg-color;
  display: grid;
  grid-template-columns: 2rem 1fr;
  border-radius: 10px;
  padding: 2px;
  outline: 1px dotted transparent;
  outline-offset: 2px;
  transition: outline 300ms ease;

  &:has(input:focus) {
    outline-color: $c-secondary;
  }

  .icon {
    font-size: 1.5rem;
  }

  input {
    background-color: transparent;
    border: none;
    outline: none;
    font-size: 1.2rem;
    color: $c-text;
    caret-color: $c-secondary;
  }
}
</style>