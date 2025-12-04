<template>
  <div class="select" :class="{ 'select--open': isOpen }" @click="toggle">
    <div class="select__header">
      <span v-if="!selected" class="select__placeholder">
        {{ placeholder }}
      </span>

      <span v-else class="select__value">
        {{ selected }}
      </span>

      <span class="select__arrow">
        <SvgSelect />
      </span>
    </div>

    <ul v-if="isOpen" class="select__list" @click.stop>
      <li
        class="select__option"
        v-for="option in options"
        :key="option"
        name="name"
        @click="choose(option)"
      >
        {{ option }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import SvgSelect from '../../assets/icons/SvgSelect.vue';

defineProps<{
  name: string;
  placeholder: string;
  options: string[];
}>();

const selected = ref<string | null>(null);
const isOpen = ref(false);

function toggle() {
  isOpen.value = !isOpen.value;
}

function choose(option: string) {
  selected.value = option;
  isOpen.value = false;
}
</script>

<style scoped lang="scss">
.select {
  position: relative;
  font: var(--font-18-regular);
  cursor: pointer;

  &__header {
    padding: 12px 10px;
    border: 1px solid var(--color-white);
    border-radius: 3px;
    background: rgba(255, 255, 255, 0.85);
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition: background 0.25s ease, border-color 0.25s ease;
  }

  &__placeholder {
    color: var(--color-blue-bg);
  }

  &__arrow {
    width: 18px;
    height: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.25s ease;

    svg {
      pointer-events: none;
      display: block;
    }
  }

  &--open {
    .select__header {
      background: var(--color-blue-dark2);
      border: 1px solid var(--color-blue-dark2);
    }

    .select__placeholder {
      color: var(--color-white);
    }

    .select__value {
      color: var(--color-white);
    }

    .select__arrow {
      transform: rotate(180deg);
    }
  }

  &__list {
    margin: 0;
    text-align: left;
    padding-inline-start: 0;
    border: 1px solid var(--color-blue-dark2);
    background: var(--color-blue-bg);
    border-radius: 6px;
    overflow-y: auto;
    max-height: 100px;

    &::-webkit-scrollbar {
      width: 6px;
    }

    &::-webkit-scrollbar-track {
      background: transparent;
    }

    &::-webkit-scrollbar-thumb {
      background: var(--color-blue-primary);
      border-radius: 6px;
    }
  }

  &__option {
    padding: 10px 14px;
    color: var(--color-white);
    transition: background 0.2s ease, color 0.15s ease;
    list-style: none;

    &:hover {
      color: var(--color-blue-link);
    }
  }
}
</style>