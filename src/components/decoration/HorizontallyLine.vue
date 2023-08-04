<template>
    <div class="hor__line" :class="{ 'reverse': reverse }">
        <div class="corner__container">
            <svg class="hor__line--corner" width="108" height="47" viewBox="0 0 108 47" fill="none"
                xmlns="http://www.w3.org/2000/svg">
                <path d="M1 0L0.999999 26C0.999998 37.0457 9.9543 46 21 46L108 46" stroke="#314373" />
                <path d="M1 0L0.999999 26C0.999998 37.0457 9.9543 46 21 46L108 46" stroke="url(#paint0_linear_1222_396)" />
                <defs>
                    <linearGradient id="paint0_linear_1222_396" x1="86.6947" y1="46" x2="29.6438" y2="46"
                        gradientUnits="userSpaceOnUse">
                        <stop stop-color="#6197FF" />
                        <stop offset="1" stop-color="#6197FF" stop-opacity="0" />
                    </linearGradient>
                </defs>
            </svg>
        </div>
        <decor-circle :isActive="isActive" :direction="'hor'"></decor-circle>
        <div class="end__container">
            <div class="hor__line--end"></div>
        </div>
    </div>
</template>

<script>
import DecorCircle from './DecorCircle.vue'
export default {
    components: {
        DecorCircle
    },
    props: {
        isActive: {
            type: Boolean,
            default: false
        },
        reverse: {
            type: Boolean,
            default: false
        }
    }
}
</script>

<style lang="scss" scoped>
.hor__line {
    position: absolute;
    left: 7%;
    top: 30%;
    display: flex;
    align-items: flex-end;
    justify-content: center;

    @media screen and (min-width: 961px) {
        left: 49.8%;
    }

    .corner__container {
        margin-bottom: -1px;
    }

    .end__container {
        height: 11px;
        display: flex;
        align-items: center;
    }

    &--end {
        height: 1px;
        background: linear-gradient(90deg, #6197FF 0%, #314373 60%);

        @media screen and (min-width: 320px) {
            display: none;
        }

        @media screen and (min-width: 768px) {
            width: 13px;
            display: block;
        }

        @media screen and (min-width: 1200px) {
            width: 56px;
        }
    }
}

.reverse {
    transform: rotate(0deg);
    left: 7%;

    @media screen and (min-width: 961px) {
        transform: rotateY(180deg);
        left: 3%;
    }

    @media screen and (min-width: 1200px) {
        left: 4.35%;
    }
}
</style>