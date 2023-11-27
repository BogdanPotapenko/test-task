<template>
  <button class="button">
    <span class="button-value"> {{ value }}</span>
  </button>
</template>

<script setup>
defineProps(["value"]);
</script>

<style lang="scss" scoped>
.button {
  display: inline-flex;
  padding: 17px 56px 15px 56px;
  justify-content: center;
  align-items: center;
  gap: 8px;
  border-radius: 56px;
  background: $gold;
  backdrop-filter: blur(10px);
  &:hover {
    background: $main;
  }
  &-value {
    color: $black;
    text-align: center;
    font-family: Gotham Pro;
    font-size: calc(14px + (20 - 14) * ((100vw - 375px) / (1920 - 375)));
    font-style: normal;
    font-weight: 700;
    line-height: 24px;
    text-transform: uppercase;
  }
}
</style>
