<template>
  <button
    class="btn"
    :class="[
      `btn--${variant}`,
      `btn--${size}`
    ]"
  >
    <span v-if="$slots.icon" class="btn__icon">
      <slot name="icon" />
    </span>

    <span class="btn__text">{{ text }}</span>
  </button>
</template>

<script setup lang="ts">
interface ButtonProps {
  text: string;
  variant?: "primary" | "secondary";
  size?: "lg" | "md";
}

withDefaults(defineProps<ButtonProps>(), {
  variant: "primary",
  size: "md"
});
</script>

<style scoped lang="scss">
.btn {
  border-radius: 4px;
  transition: 0.2s ease;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  text-transform: uppercase;
  gap: 10px; /* ← отступ между иконкой и текстом */
}

.btn__icon {
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn__text {
  display: inline-block;
}

.btn--primary {
  background: var(--color-blue-primary);
  color: var(--color-white);
  border: 1px solid var(--color-white);

  &:hover {
    button { box-shadow: 2px 2px 5px var(--color-blue-dark); }
  }
}

.btn--secondary {
  background: var(--color-white);
  color: var(--color-grey);
  border: 1px solid var(--color-grey-dark);

  &:hover {
    button { box-shadow: 2px 2px 5px var(--color-grey); }
  }
}

.btn--lg {
  padding: 17px 32px;
  font: var(--font-15-regular);
}

.btn--md {
  padding: 15px 32px;
  font: var(--font-13-regular);
}
</style>