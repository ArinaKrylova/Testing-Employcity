<template>
    <div class="icon">
        <div class="icon__circle">
            <component :is="icon" class="icon__circle-svg" />
        </div>
        <h5 class="icon__text" v-html="text"></h5>
    </div>
</template>

<script setup lang="ts">
defineProps<{
    icon: any,
    text: string
}>()
</script>

<style scoped lang="scss">
.icon {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: var(--space-20);
    width: 209px;

    &__circle {
        width: 100px;
        height: 100px;
        background-color: var(--color-blue-primary);
        border: 5px solid var(--color-blue-dark);
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;

    }

    &__text {
        color: var(--color-white);
        text-align: center;
    }
}
</style>