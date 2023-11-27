<template>
  <button class="button">
    <span class="default-text"> {{ value }}</span>
  </button>
</template>

<script setup>
defineProps(["value"]);
</script>

<style lang="scss" scoped>
.button {
  display: flex;
  width: 100%;
  padding: 16px;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  background: $lightgold;
  &:hover {
    background: $main;
  }
  &:disabled {
    background: $gray800;
    cursor: default;
  }
  &-value {
    color: $gray500;
    text-align: center;
  }
}
</style>
