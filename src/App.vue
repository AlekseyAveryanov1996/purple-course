<script setup>
  import Button from "/src/components/Button.vue";
  import Header from './components/Header.vue'
  import Card from './components/Card.vue'
  import { ref } from "vue";

  const countValue = ref(1);

  const valueCard = ref(
    [
      {
        word: 'unadmitted',
        translation: 'непризнанный',
        status: 'pending',
      },
      {
        word: 'armour-piercer',
        translation: 'бронебойщик',
        status: 'pending-translate',
      },
      {
        word: 'stamen',
        translation: 'тычинка',
        status: 'sucsess',
      },
      {
        word: 'vino',
        translation: 'вино',
        status: 'falied',
      },
    ]
  )

</script>

<template>
  <Header />
  <main class="main">
    <Button class="start-game">
      Начать игру
    </Button>
  </main>

  <div class="pole-cards">
    <Card v-for='(card, index) in valueCard' :key='index' :number='"0" + (index + 1)'
      :label='card.word'
      :status='card.status'
      :translation='card.translation'
      @resize-card='(data) => console.log(data)' @status-card='(data) => console.log(data)'
    />
  </div>



</template>

<style scoped>
  .pole-cards {
    display: grid;
    grid-template-columns: repeat(4, minmax(0px, 1fr));
    column-gap: 107px;
    row-gap: 66px;
    max-width: 1350px;
    margin-left: auto;
    margin-right: auto;
  }

  .start-game {
    max-width: 335px;
    margin-left: auto;
    margin-right: auto;
  }

</style>
