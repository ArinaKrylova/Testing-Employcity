<template>
    <section class="main" :style="{ backgroundImage: `url(${bg})` }">
        <div class="main__inner container">
            <h1 class="main__title"><span>Lorem ipsum</span> dolor sit <br />
                amet consectetur <span>adipiscing</span>
            </h1>

            <div class="main__contant">
                <p class="main__contant-text">At vero eos et accusamus et iusto odio dignissimos ducimus!</p>
                <ul class="main__contant-list">
                    <li>Totam rem aperiam eaque ipsa</li>
                    <li>Sit voluptatem accusantium doloremque laudantium</li>
                    <li>Sed ut perspiciatis, unde omnis iste natus error</li>
                </ul>
            </div>

            <div class="main__btn">
                <Button class="main__btn-btn" text="заказать" />
                <Button class="main__btn-btn" text="подробнее" variant="secondary" />
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import bg from '@/assets/img/main.webp'
import Button from '../ui/Button.vue';
</script>

<style scoped lang="scss">
.main {
    width: 100%;
    height: 850px;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;

    &__inner {
        padding-top: 203px;

        @include mobile {
            padding-top: 150px;
        }
    }

    &__title {
        text-transform: uppercase;

        span {
            color: var(--color-blue-primary);
        }
    }

    &__contant {
        &-text {
            font: var(--font-20-bold);
        }

        ul {
            padding-left: 20px;
        }

        ul li {
            position: relative;
            margin-bottom: 5px;
        }

        ul li::before {
            content: "";
            position: absolute;
            left: -15px;
            top: 10px;
            width: 5px;
            height: 2px;
            background: var(--color-black);
        }

        &-list {
            font: var(--font-20-regular);
        }
    }

    &__btn {
        display: flex;
        gap: var(--space-30);

        &-btn {
            width: 183px;

        }

        @include mobile {
            flex-direction: column;
            gap: var(--space-15);

            &-btn {
                width: 100%;

            }
        }
    }

    &__contant,
    &__btn {
        padding-top: var(--space-80);

        @include tablet {
            padding-top: var(--space-30);
        }

        @include mobile {
            padding-top: var(--space-15);
        }
    }


}
</style>