<script setup lang="ts">
import { ref } from 'vue'

const supabase = useSupabaseClient()

import Input from '../components/Input.vue'
import Button from '../components/Button.vue'

const email = ref('')
const password = ref('')
const loading = ref(false)

async function handleLogin(e) {
  e.preventDefault()

  try {
    loading.value = true
    const { error } = await supabase.auth.signInWithPassword({ email: email.value, password: password.value })
    if (error) throw error
  } catch (error) {
    alert(error.error_description || error.message)
  } finally {
    loading.value = false
  }
}
</script>

<template>
  <main>
    <section>
      <h1>Faça login para continuar</h1>
      <form @submit="handleLogin">
        <Input
          type="email"
          id="email-input"
          icon="ph:at"
          v-model="email"
          placeholder="Email"
          required
        />

        <Input
          type="password"
          id="password-input"
          icon="ph:lock"
          v-model="password"
          placeholder="Senha"
          required
        />

        <Button
          type="submit"
          :loading="loading"
        >
          Entrar
        </Button>
      </form>

      <article>
        <p>Não possuí uma conta?</p>
        <p>Então <NuxtLink to="/register">clique aqui</NuxtLink> e crie uma!</p>
      </article>
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

    article {
      background-color: $bg-color;
      margin-top: 0.5rem;
      padding: 1rem;
      text-align: center;
      font-size: 1rem;
      border-radius: 10px;

      a {
        color: $c-secondary;
      }
    }
  }
}
</style>