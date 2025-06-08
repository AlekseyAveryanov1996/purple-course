<script setup>
  import Scope from './Score.vue'
</script>

<template>
  <header class="header">
    <div class="container header__container">
      <div class="header__logo">Запомни слово</div>
      <Scope scopeValue=10 />
    </div>
  </header>
</template>

<style scoped>
  .header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    padding-top: 40px;
  }

  .header__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .header__logo {
    font-size: 16px;
    line-height: 24px;
    letter-spacing: 12%;
    color: var(--colorGray);
    text-transform: uppercase;
  }
</style>
