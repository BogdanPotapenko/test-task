<template>
  <div class="main">
    <SectionHero></SectionHero>
  </div>
</template>

<script setup>
import SectionHero from "./components/sections/SectionHero.vue";
</script>

<style lang="scss" scoped>
.main {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 100px;
  margin: 0 auto;
}
</style>
