<script setup lang="ts">
import { Icon } from '@iconify/vue'
</script>

<template>
  <button
    :class="loading ? 'loading' : null"
    :disabled="loading"
  >
    <Icon
      icon="ph:circle-notch-bold"
      class="icon"
      v-if="loading"
    />
    <span v-else>
      <slot />
    </span>
  </button>
</template>

<script lang="ts">
  export default {
    props: {
      loading: {
        type: Boolean,
        default: false,
      },
    }
  }
</script>

<style scoped lang="scss">
@import '@/assets/colors.scss';

button {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.3rem;
  font-size: 1.4rem;
  background-color: $c-accent;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: all 300ms ease;

  &:hover:not(.loading) {
    background-color: $c-secondary;
  }
  
  &.loading {
    max-width: fit-content;
    aspect-ratio: 1 / 1;
    margin-inline: auto;
    cursor: auto;
    color: $bg-color;
  }
}

.icon {
  animation: spin 1s infinite;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}
</style>