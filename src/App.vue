<script setup>
  import Button from "/src/components/Button.vue";
  import Header from './components/Header.vue'
  import Card from './components/Card.vue'
</script>

<template>
  <Header />
  <main class="main">
    <Button>
      Начать игру
    </Button>
  </main>

  <Card number='01' label='unadmitted' @resize-card='(data) => console.log(data)' @status-card='(data) => console.log(data)'/>

</template>

<style scoped>

</style>
