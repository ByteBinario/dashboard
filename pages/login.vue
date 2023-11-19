<script setup lang="ts">
import { ref } from 'vue'

import Input from '../components/Input.vue'
import Button from '../components/Button.vue'

const email = ref('')
const password = ref('')
const loading = ref(false)
</script>

<template>
  <main>
    <section>
      <h1>Faça login para continuar</h1>
      <form>
        <Input
          type="email"
          id="email-input"
          icon="ph:at"
          v-model="email"
          required
        />

        <Input
          type="password"
          id="password-input"
          icon="ph:lock"
          v-model="password"
          required
        />

        <Button
          :loading="loading"
          @click="loading = !loading"
        >
          Entrar
        </Button>
      </form>
    </section>
  </main>
</template>

<style scoped lang="scss">
@import '@/assets/colors.scss';

main {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100dvh;

  section {
    padding: 1rem;
    border: 1px solid $c-primary;
    border-radius: 10px;
    background-color: $bg-color-s;
    box-shadow: 5px 5px 15px rgb(0 0 0 / 50%);

    form {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      margin-top: 1rem;
    }
  }
}
</style>