<template>
  <label :for="label" class="container">
    <input
      :type="type"
      :id="label"
      placeholder=" "
      :value="modelValue"
      @input="updateValue"
      autocomplete="off"
      class="input default-text"
      :class="error && modelValue.length > 0 ? 'input-error' : ''"
    />
    <span class="icon"><slot /></span>
    <span
      class="label default-text"
      :class="modelValue.length > 0 ? 'input-valid' : ''"
    >
      {{ label }}
    </span>
    <span v-if="error && modelValue.length > 0" class="error">
      {{ error }}
    </span>
  </label>
</template>

<script setup>
const emit = defineEmits(["update:modelValue"]);

defineProps(["label", "type", "error", "modelValue"]);

const updateValue = (e) => {
  emit("update:modelValue", e.target.value);
};
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  display: flex;
  width: 100%;
  align-items: center;
  gap: 8px;
  background: $gray900;
  &:hover > .input {
    outline: none;
    border: 1px solid $main;
    box-shadow: 0px 0px 6px 0px rgba(252, 252, 252, 0.32);
    -webkit-box-shadow: 0px 0px 6px 0px rgba(252, 252, 252, 0.32);
    -moz-box-shadow: px 0px 6px 0px rgba(252, 252, 252, 0.32);
  }
  .input {
    width: 100%;
    padding: 15px 15px 15px 40px;
    border-radius: 8px;
    border: 1px solid $gray400;
    background: $gray900;
    color: $main;
    &:focus-visible {
      outline: none;
      border: 1px solid $main;
      box-shadow: 0px 0px 6px 0px rgba(252, 252, 252, 0.32);
      -webkit-box-shadow: 0px 0px 6px 0px rgba(252, 252, 252, 0.32);
      -moz-box-shadow: px 0px 6px 0px rgba(252, 252, 252, 0.32);
    }
    &:focus ~ .label,
    ~ .input-valid {
      background-color: $gray900;
      left: 16px;
      top: -8px;
      padding: 0 4px;
      font-size: 10px;
      line-height: 160%;
      letter-spacing: 0.2px;
    }
  }
  .input-error {
    border: 1px solid $error;
    box-shadow: none;
    -webkit-box-shadow: none;
    &:hover {
      border: 1px solid $error;
      box-shadow: none;
      -webkit-box-shadow: none;
    }
    &:focus-visible {
      border: 1px solid $error;
      box-shadow: none;
      -webkit-box-shadow: none;
    }
  }
  .icon {
    position: absolute;
    left: 16px;
    flex-shrink: 0;
  }
  .label {
    position: absolute;
    left: 40px;
    background: $gray900;
    color: $gray100;
  }
  .error {
    background: $gray900;
    position: absolute;
    right: 8px;
    bottom: -7px;
    display: flex;
    padding: 0px 4px;
    justify-content: center;
    align-items: center;
    gap: 8px;
    color: $error;
    font-variant-numeric: lining-nums proportional-nums;
    font-feature-settings: "ss09" on;
    font-family: Stolzl;
    font-size: 10px;
    font-style: normal;
    font-weight: 400;
    line-height: 160%;
    letter-spacing: 0.2px;
  }
}
</style>

https://bogdanpotapenko.github.io/test-task/assets/logo-870A2ySR.svg
https://bogdanpotapenko.github.io/test-task/assets/icons/email.svg
