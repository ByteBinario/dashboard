<template>
  <main>
    <section>
      <h1>Faça login para continuar</h1>
      <form>

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
  }
}
</style>