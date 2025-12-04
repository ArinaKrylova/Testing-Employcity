<template>
    <section class="order" :style="{ backgroundImage: `url(${bg2})` }">
        <div class="order__inner container">
            <h2 class="order__title">Оформление <span>Заказа</span></h2>
            <p class="order__subtitle">Перед заполнением формы ознакомьтесь с нашей схемой работы!</p>

            <div class="order__icons">
                <Icon v-for="(item, index) in steps" :key="index" :icon="item.icon" :text="item.text" />
            </div>

            <div class="order__params">
                <Select name="systemType" class="order__params-grid grid-1" placeholder="Выберите тип системы"
                    :options="systemOptions" />
                <Input name="email" class="order__params-grid grid-2" placeholder="Ваш e-mail" />
                <Input name="name" class="order__params-grid grid-3" placeholder="Ваше имя" />
                <Slider name="volume" class="order__params-grid grid-4"
                    label="Sed ut perspiciatis, unde omnis iste natus" />
                <Button class="order__params-grid grid-5" text="Прикрепить файл" variant="secondary">
                    <template #icon>
                        <SvgFile2 />
                    </template>
                </Button>
            </div>

            <Button type="submit" class="order__btn" text="Отправить" size="lg" />
        </div>
    </section>
</template>

<script setup lang="ts">
import { steps } from '../../data/circle';
import Icon from '../ui/Icon.vue';
import Input from '../ui/Input.vue';
import Select from '../ui/Select.vue';
import Slider from '../ui/Slider.vue';
import Button from '../ui/Button.vue';
import SvgFile2 from '../../assets/icons/SvgFile2.vue';
import bg2 from '../../assets/img/order.png'

const systemOptions = [
    'Sed ut perspiciatis',
    'Nemo enim ipsam',
    'Et harum quidem',
    'Temporibus autem',
    'Itaque earum rerum'
];
</script>

<style scoped lang="scss">
.order {
    background-color: var(--color-blue-bg);
    padding: 120px 0 150px;

    &__inner {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    &__title {
        color: var(--color-white);
        text-transform: uppercase;

        span {
            color: var(--color-blue-primary);
        }
    }

    &__subtitle {
        font: var(--font-18-regular);
        color: var(--color-grey-light);
        padding-top: var(--space-30);
    }

    &__icons {
        padding-top: var(--space-80);
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: var(--space-30);
    }

    &__icons>* {
        position: relative;
    }

    &__icons>*:not(:last-child)::after {
        content: "";
        position: absolute;
        top: 25%;
        right: -65px;
        width: 100px;
        height: 8px;

        background:
            radial-gradient(circle, var(--color-grey-light) 4px, transparent 4px) 0% center,
            radial-gradient(circle, var(--color-grey-light) 4px, transparent 4px) 25% center,
            radial-gradient(circle, var(--color-grey-light) 4px, transparent 4px) 50% center,
            radial-gradient(circle, var(--color-grey-light) 4px, transparent 4px) 75% center,
            radial-gradient(circle, var(--color-grey-light) 4px, transparent 4px) 100% center;

        background-size: 8px 8px;
        background-repeat: no-repeat;

    }

    @media screen and (max-width: 1205px) {
        &__icons>*::after {
            display: none;
        }
    }

    &__params {
        padding-top: var(--space-80);
        display: grid;
        justify-items: stretch;
        gap: var(--space-30);
        grid-template-columns: repeat(3, 370px);
        grid-template-rows: repeat(2, 48px);
        grid-template-areas:
            'grid-1 grid-2 grid-3'
            'grid-4 grid-4 grid-5'
        ;

        @include desktop {
            grid-template-columns: repeat(2, 350px);
            grid-template-rows: repeat(3, 48px);
            grid-template-areas:
                'grid-1 grid-2'
                'grid-4 grid-4'
                'grid-3 grid-5'
            ;
        }

        @include tablet {
            grid-template-columns: repeat(1, 450px);
            grid-template-rows: repeat(3, 48px);
            grid-template-areas:
                'grid-1'
                'grid-2'
                'grid-3'
                'grid-4'
                'grid-5'
            ;
        }

        @include mobile {
            grid-template-columns: repeat(1, 1fr);
        }
    }

    &__btn {
        margin-top: var(--space-40);
        max-width: 370px;
        width: 100%;
    }

}

.grid-1 {
    grid-area: grid-1;
}

.grid-2 {
    grid-area: grid-2;
}

.grid-3 {
    grid-area: grid-3;
}

.grid-4 {
    grid-area: grid-4;
}

.grid-5 {
    grid-area: grid-5;
}
</style>