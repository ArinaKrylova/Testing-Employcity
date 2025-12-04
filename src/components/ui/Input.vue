<template>
  <div class="input">
    <input
      :name="name"
      class="input__field"
      :placeholder="placeholder"
      type="text"
    />
  </div>
</template>

<script setup lang="ts">
defineProps<{
  name: string;
  placeholder: string;
}>();
</script>

<style scoped lang="scss">
.input {
  &__field {
    width: -webkit-fill-available;
    padding: 12px 10px;
    border: 1px solid var(--color-white);
    border-radius: 3px;
    background: rgba(255, 255, 255, 0.85);
    font: var(--font-18-regular);
    outline: none;
    transition: border-color 0.25s ease, background 0.25s ease;

    &::placeholder {
      color: var(--color-blue-bg);
      opacity: 1;
    }
  }
}
</style>