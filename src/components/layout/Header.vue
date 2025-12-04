<template>
    <header class="header">
        <div class="header__inner container">
            <a href="#" class="header__logo logo">
                <SvgLogo />
            </a>

            <nav class="header__menu">
                <ul class="header__menu-list" :class="{ open: isOpen }">
                    <li v-for="item in menuItems" :key="item.label" class="header__menu-item">
                        <a href="item.href" class="header__menu-link">{{ item.label }}</a>
                    </li>
                </ul>
            </nav>

            <button class="burger" :class="{ open: isOpen }" @click="isOpen = !isOpen">
                <span></span><span></span><span></span>
            </button>
        </div>
    </header>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import SvgLogo from '../../assets/icons/SvgLogo.vue';

const isOpen = ref(false);

const menuItems = [
    { label: "Бизнес", href: "#" },
    { label: "О нас", href: "#" },
    { label: "Цены", href: "#" },
    { label: "Оформить заказ", href: "#" },
];

</script>

<style scoped lang="scss">
.header {
    z-index: 100;
    position: fixed;
    top: 0;
    width: 100%;
    background: var(--color-bg);
    padding: 33px 0 33px;

    &__inner {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    &__menu {
        &-list {
            display: flex;
            gap: 60px;

            @include tablet-s {
                position: absolute;
                top: 90px;
                right: 0;
                left: 0;
                max-width: 100%;
                background: var(--color-bg);
                padding: 30px;
                flex-direction: column;
                text-align: center;
                gap: 25px;
                opacity: 0;
                visibility: hidden;
                transform: translateX(20%);
                transition: 0.3s ease;
                border-radius: 12px;

                &.open {
                    opacity: 1;
                    visibility: visible;
                    transform: translateX(0);
                }
            }
        }
    }
}

.burger {
    display: none;
    flex-direction: column;
    justify-content: center;
    gap: 6px;
    width: 32px;
    height: 32px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;
    z-index: 10;

    span {
        display: block;
        height: 3px;
        width: 100%;
        background: #fff;
        border-radius: 2px;
        transition: 0.3s ease;
    }

    &.open span:nth-child(1) {
        transform: translateY(9px) rotate(45deg);
    }

    &.open span:nth-child(2) {
        opacity: 0;
    }

    &.open span:nth-child(3) {
        transform: translateY(-9px) rotate(-45deg);
    }

    @include tablet-s {
        display: flex;
    }
}
</style>