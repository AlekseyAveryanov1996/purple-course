<script setup></script>

<template>
  <button>
    <slot></slot>
  </button>
</template>

<style scoped>
  button {
    padding: 16px 10px;
    border-radius: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: var(--colorWhite);
    font-size: 24px;
    line-height: 36px;
    min-width: 335px;
    background: var(--colorBlue);
    border: none;
    outline: none;
    cursor: pointer;
  }
  button:hover {
    background: #006FCB;
  }
</style>
