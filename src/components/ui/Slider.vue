<template>
  <div class="slider">
    <div class="slider__top">
      <span class="slider__label">{{ label }}</span>
      <span class="slider__value">{{ model }} %</span>
    </div>

    <div class="slider__wrap">
      <input class="slider__input" name="name" type="range" :min="min" :max="max" v-model="model" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";

const props = defineProps<{
  name: string | number;
  label: string;
  min?: number;
  max?: number;
  modelValue?: number;
}>();

const emit = defineEmits(["update:modelValue"]);

const model = ref(props.modelValue ?? 0);

watch(model, val => emit("update:modelValue", val));
</script>

<style scoped lang="scss">
.slider {
  &__top {
    font: var(--font-18-regular);
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 8px;
    gap: 10px;

    @include tablet {
      flex-wrap: wrap;
      justify-content: center;
    }
  }

  &__label {
    font: var(--font-24-regular);
    color: var(--color-white);
  }

  &__value {
    font: var(--font-24-regular);
    color: var(--color-white);
  }

  &__wrap {
    width: 100%;
  }

  &__input {
    width: 100%;
    -webkit-appearance: none;
    height: 10px;
    border-radius: 10px;
    background-color: var(--color-grey-light);
    border: 1px solid var(--color-white);
    outline: none;
    cursor: pointer;
  }

  &__input::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 23px;
    height: 23px;
    background: var(--color-blue-primary);
    border-radius: 50%;
    border: 3px solid var(--color-blue-dark);
  }
}
</style>