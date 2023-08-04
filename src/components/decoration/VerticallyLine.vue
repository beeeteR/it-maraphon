<template>
    <div class="container__line">
        <decor-circle :isActive="isActive" :direction="'vert'"></decor-circle>
        <div class="vert__line"></div>
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
        }
    }
}
</script>

<style lang="scss">
.container__line {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 5;

    @media screen and (min-width: 320px) {
        margin-top: 15px;
        width: 21px;
    }

    @media screen and (min-width: 768px) {
        margin-top: 24px;
        width: 24px;
    }

    @media screen and (min-width: 1200px) {
        margin-top: 35px;
    }


    .vert__line {
        position: relative;
        width: 1px;
        height: 100%;
        min-height: 166px;
        background: linear-gradient(180deg, #6197FF 0%, #314373 60%);
    }
}
</style>