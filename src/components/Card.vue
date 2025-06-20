<script setup>
  import Ok from '../Icons/OkIcon.vue'
  import Falid from '../Icons/FalidIcon.vue'

  const props = defineProps({
    number: String,
    label: String,
    score: Number,
    status: String,
    translation: String,
  })

  const emit = defineEmits(['resize-card', 'status-card'])


  function emiterResizeCard() {
    emit('resize-card', 'pending-translate')
  }

  function emiterStatus(status) {
    emit('status-card', status)
  }



</script>

<template>
  <article class="card" :data-score='score'>
    <div class="card__number">{{number}}</div>
    <div v-if="props.status === 'pending'" class="card__label">{{label}}</div>
    <div v-else class="card__label">{{translation}}</div>

    <div class="card__footer">
      <div v-if="props.status === 'pending'" class="card__footer-resize" @click="emiterResizeCard()">Перевернуть</div>
      <div v-if="props.status === 'sucsess' || props.status === 'falied'" class="card__footer-resize" @click="emiterResizeCard()">Завершено</div>
      <div v-else-if="props.status === 'pending-translate'" class="card__footer-status">
        <div class="card__footer-status-ok card__footer-status-icon" @click="emiterStatus('sucsess')">
          <Ok />
        </div>
        <div class="card__footer-status-falid card__footer-status-icon" @click="emiterStatus('falied')">
          <Falid />
        </div>
      </div>
    </div>

    <div v-if="props.status === 'sucsess'" class="card__status-icon">
      <Ok  />
    </div>
    <div v-if="props.status === 'falied'" class="card__status-icon">
      <Falid />
    </div>

  </article>
</template>

<style>
  .card {
    padding: 28px 19px;
    border-radius: 16px;
    background: var(--colorWhite);
    position: relative;
    cursor: pointer;
    min-height: 376px;
    z-index: 1;
  }
  .card::before {
    content: '';
    position: absolute;
    top: 28px;
    left: 19px;
    width: calc(100% - 38px);
    height: calc(100% - 56px);
    border-radius: 12px;
    border: 1px solid var(--colorPrimary);
    z-index: -1;
  }
  .card:hover {
    box-shadow: 10px 10px 10px 0px #0000000D;
  }
  .card__number {
    position: absolute;
    background: var(--colorWhite);
    font-size: 14px;
    line-height: 100%;
    color: var(--colorBlack);
    top: 20px;
    left: 35px;
    z-index: 1;
  }
  .card__label {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1;
    font-size: 18px;
  }
  .card__footer {
    position: absolute;
    bottom: 15px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 1;
    background: var(--colorWhite);
    min-width: 89px;
    min-height: 24px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .card__footer-resize {
    font-size: 12px;
    font-weight: 700;
    text-transform: uppercase;
    text-align: center;
  }

  .card__footer-status {
    position: absolute;
    z-index: -1;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    top: 0;
    left: 0;
  }

  .card__footer-status-icon {
    display: flex;
  }

  .card__status-icon {
    position: absolute;
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    width: 36px;
    height: 36px;
  }

  .card__status-icon svg {
    width: 100%;
    height: 100%;
  }



</style>
