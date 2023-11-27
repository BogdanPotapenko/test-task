<template>
  <div
    class="popup"
    :class="isPopup ? 'popup-active' : ''"
    @click="modalClose()"
  >
    <div class="container" @click.stop>
      <button class="popup-button" @click="modalClose()"></button>
      <div class="popup-content"><slot /></div>
    </div>
  </div>
</template>

<script setup>
defineProps(["isPopup"]);
const emit = defineEmits(["close"]);

const modalClose = () => {
  emit("close");
};
</script>

<style lang="scss" scoped>
.popup {
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 10;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  padding: 27px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(7.5px);
  transition-duration: 700ms;
  -webkit-transition-duration: 700ms;
  visibility: hidden;
  opacity: 0;
  @media (max-width: 375px) {
    padding: 23px 30px 23px 27px;
  }
  &-active {
    visibility: visible;
    opacity: 1;
  }
  .container {
    position: relative;
    width: 100%;
    height: 100%;
    max-width: 720px;
    overflow: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 16px;
    background: $gray900;
    box-shadow: 0px 4px 24px 0px rgba(21, 19, 14, 0.64);
    @media (min-width: 1025px) {
      max-height: 704px;
    }

    .popup-button {
      width: 40px;
      height: 40px;
      position: absolute;
      top: 16px;
      right: 16px;
      cursor: pointer;
      z-index: 11;
      border-radius: 8px;
      background: url(../../assets/icons/cross.svg);
      background-size: 100%;
      &:hover {
        border: 1px solid $gray100;
      }
      @media (max-width: 640px) {
        width: 23px;
        height: 23px;
        top: 10px;
        right: 10px;
      }
    }
    .popup-content {
      width: 100%;
      height: 100%;
    }
  }
}
</style>
