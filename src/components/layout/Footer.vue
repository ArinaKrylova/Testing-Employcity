<template>
    <footer class="footer">
        <div class="footer__inner container">
            <p class="footer__text">© 2018 «LoremIpsum.net» Все права защищены.</p>

            <div class="footer__pay">
                <div class="footer__pay-item">
                    <Qiwi />
                    <span>Qiwi wallet</span>
                </div>
                <div class="footer__pay-item">
                    <YandexMoney />
                    <span>Yandex Money</span>
                </div>
                <div class="footer__pay-item">
                    <WebMoney />
                    <span>Web Money</span>
                </div>
            </div>

            <div class="footer__social">

                <a href="#" class="footer__social-item">
                    <Email />
                    info@ipsum228.com
                </a>
                <a href="#" class="footer__social-item">
                    <Bk />
                    Мы вконтакте
                </a>
            </div>

        </div>

    </footer>
</template>

<script setup lang="ts">
import Qiwi from '../../assets/icons/pay/Qiwi.vue';
import WebMoney from '../../assets/icons/pay/WebMoney.vue';
import YandexMoney from '../../assets/icons/pay/YandexMoney.vue';
import Bk from '../../assets/icons/social/Bk.vue';
import Email from '../../assets/icons/social/Email.vue';
</script>

<style scoped lang="scss">
.footer {
    font: var(--font-13-regular);
    background-color: var(--color-blue-dark2);
    padding: 30px 0;

    &__inner {
        display: flex;
        gap: 38px;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    &__text {
        color: var(--color-white);
    }

    &__pay {
        color: var(--color-grey-light);
    }

    &__pay,
    &__social {
        display: flex;
        gap: 30px;
        flex-wrap: wrap;
        align-items: center;

        &-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }
    }

}
</style>