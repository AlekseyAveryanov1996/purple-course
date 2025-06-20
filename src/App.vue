<script setup>
import Button from "/src/components/Button.vue";
import Header from './components/Header.vue'
import Card from './components/Card.vue'
import { computed, onMounted, ref } from "vue";

const countValue = ref(1);

const valueCard = ref(null
  // [
  //   {
  //     word: 'unadmitted',
  //     translation: 'непризнанный',
  //     status: 'pending',
  //   },
  //   {
  //     word: 'armour-piercer',
  //     translation: 'бронебойщик',
  //     status: 'pending-translate',
  //   },
  //   {
  //     word: 'stamen',
  //     translation: 'тычинка',
  //     status: 'sucsess',
  //   },
  //   {
  //     word: 'vino',
  //     translation: 'вино',
  //     status: 'falied',
  //   },
  // ]
)



async function getCards() {
  const response = await fetch('http://localhost:8080/api/random-words');
  if (response.status !== '200') {
    valueCard.value = null;
    return
  } else {
    const data = await response.json();
    valueCard.value = data.map(item => {
      return {
        word: item.word,
        translation: item.translation,
        status: 'pending',
      }
    })
  }




}

</script>

<template>
  <Header />
  <main v-if='valueCard === null' class="main">
    <Button @click='getCards()' class="start-game">
      Начать игру
    </Button>
  </main>

  <div v-else class="pole-cards">
    <Card v-for='(card, index) in valueCard' :key='index' :number='(index <= 8) ? "0" + (index + 1) : (index + 1)' :label='card.word'
    :status='card.status' :translation='card.translation' @resize-card='(data) => valueCard[index].status = data'
    :score="0"
    @status-card='(data) => valueCard[index].status = data' />

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
  margin-top: 100px;
  margin-bottom: 100px;
}

.start-game {
  max-width: 335px;
  margin-left: auto;
  margin-right: auto;
}
</style>
