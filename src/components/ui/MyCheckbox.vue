<template>
  <div class="container">
    <input
      type="checkbox"
      id="checkbox"
      :value="modelValue"
      @click="update"
      class="checkbox"
      required
    />
    <label class="label" for="checkbox"></label>
  </div>
</template>

<script setup>
const emit = defineEmits(["update"]);

defineProps(["modelValue"]);

const update = () => {
  emit("update");
};
</script>

<style lang="scss" scoped>
.container {
  max-width: 18px;
  max-height: 18px;

  .checkbox {
    padding: 0;
    display: none;
    cursor: pointer;
  }
  .label {
    width: 18px;
    height: 18px;
    display: block;
    cursor: pointer;
    border-radius: 2px;
    border: 1px solid $gray100;
    &:hover {
      border-radius: 2px;
      border: 1px solid $main;
    }
  }
  .checkbox:checked + .label {
    border: none;
  }
  .checkbox:checked + .label:after {
    content: "";
    display: block;
    width: 18px;
    height: 18px;
    background: url(../../assets/icons/checkbox.svg);
  }
}
</style>
