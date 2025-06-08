<script setup>
  import LikeIcons from '../Icons/LikeIcons.vue'

  const props = defineProps({
    scopeValue: Number,
  })

</script>

<template>
  <div class="scope">
    <div class="scope__count">
      {{ scopeValue }}
    </div>
    <div class="scope__icon">
      <LikeIcons />
    </div>
  </div>
</template>

<style scoped>
  .scope {
    display: flex;
    align-items: center;
    padding: 12px 24px;
    border-radius: 36px;
    background: var(--colorPrimary);
    box-shadow: 0px 0px 4px 0px #00000026;
    gap: 10px;
  }
  .scope__count {
    font-weight: 700;
    color: var(--colorBlue);
    font-size: 16px;
    line-height: 24px;
  }
  .scope__icon {
    display: flex;
    flex-shrink: 0;
  }
</style>
