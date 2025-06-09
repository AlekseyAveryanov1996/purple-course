<script setup>
  import Button from "/src/components/Button.vue";
  import Header from './components/Header.vue'
  import Card from './components/Card.vue'
  import { ref } from "vue";

  const countValue = ref(1);

  const valueCard = ref({
    word: 'unadmitted',
    traslation: 'непризнанный',
    state: 'closed',
    status: '',
  })

</script>

<template>
  <Header />
  <main class="main">
    <Button>
      Начать игру
    </Button>
  </main>

  <Card number='01'
    :label='valueCard.word'
    :state='valueCard.state'
    :status='valueCard.status'
    @resize-card='(data) => console.log(data)' @status-card='(data) => console.log(data)'
  />

</template>

<style scoped>

</style>
