<template>
    <div class="history__item" :class="{ 'history__item--active': isActive }">
        <h1 class="year">{{ page.year }}</h1>
        <h2 class="title">{{ page.title }}</h2>
        <div class="desc__container">
            <div class="lines">
                <vertically-line :isActive="isActive"></vertically-line>
                <horizontally-line :isActive="isActive" :reverse="checkID()"></horizontally-line>
            </div>
            <p class="desc" :class="{ 'grid-row1': page.id % 2 != 0 }">{{ page.desc }}</p>
        </div>
        <div class="item__circles" :class="{ 'scale0': !isActive }">
            <div class="item__circles--content">
                <div class="external__circle"></div>
                <div class="internal__circle"></div>
            </div>
        </div>
    </div>
</template>

<script>
import { useMainStore } from '@/stores/store'
import VerticallyLine from './decoration/VerticallyLine.vue'
import HorizontallyLine from './decoration/HorizontallyLine.vue'

export default {
    components: {
        VerticallyLine,
        HorizontallyLine
    },
    props: {
        page: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            store: useMainStore()
        }
    },
    methods: {
        checkID() {
            if (this.page.id % 2 != 0) {
                return true
            }
            return false
        }
    },
    computed: {
        isActive() {
            if (this.store.getCurrentPage == this.page.id) {
                return true
            }
            return false
        }
    }
}
</script>

<style lang="scss">
.history__item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
    align-items: flex-start;

    @media screen and (min-width: 320px) {
        margin-bottom: 10px;
    }

    @media screen and (min-width: 768px) {
        margin-bottom: 24px;
    }

    @media screen and (min-width: 961px) {
        align-items: center;
    }

    @media screen and (min-width: 1200px) {
        margin-bottom: 0px;
    }

    .year,
    .title,
    .desc {
        color: #6176AD;
    }

    .year {
        font-weight: 400;


        @media screen and (min-width: 320px) {
            font-size: 16px;
            line-height: 135%;
        }

        @media screen and (min-width: 576px) {
            font-size: 30px;
        }

        @media screen and (min-width: 768px) {
            font-size: 40px;
            line-height: 135%;
        }

        @media screen and (min-width: 1200px) {
            font-size: 46px;
        }
    }

    .title {
        font-size: 20px;
        font-weight: 600;

        @media screen and (min-width: 320px) {
            font-size: 14px;
            font-weight: 400;
            line-height: 155%;
        }

        @media screen and (min-width: 576px) {
            font-size: 18px;
        }

        @media screen and (min-width: 768px) {
            font-size: 20px;
            font-weight: 600;
            line-height: 30px;
        }

        @media screen and (min-width: 1200px) {
            line-height: 28px;
        }
    }

    .desc__container {
        display: flex;
        
        @media screen and (min-width: 961px) {
            display: grid;
            grid-template-columns: 1fr auto 1fr;
        }

        .lines {
            position: relative;
            display: flex;
            justify-content: flex-start;
            min-width: 130px;
            grid-column: 2;

            @media screen and (min-width: 320px) {
                min-width: 136px;
            }

            @media screen and (min-width: 768px) {
                min-width: 165px;
            }

            @media screen and (min-width: 961px) {
                min-width: 280px;
                justify-content: center;
            }

            @media screen and (min-width: 1200px) {
                min-width: 380px;
            }
        }

        .desc {
            align-self: center;
            font-size: 16px;
            font-weight: 400;

            @media screen and (min-width: 320px) {
                font-size: 10px;
                font-weight: 400;
                line-height: 12px;
            }

            @media screen and (min-width: 576px) {
                font-size: 12px;
                line-height: 16px;
            }

            @media screen and (min-width: 768px) {
                font-size: 16px;
                line-height: 24px;
            }
        }
    }

    .item__circles {
        position: absolute;
        width: 100%;
        margin-bottom: 30%;
        display: flex;
        flex-direction: column;
        align-items: center;
        transform: scale(100%);
        transition: all 500ms;

        &--content {
            width: 287px;
            position: relative;
        }

        .external__circle,
        .internal__circle {
            position: absolute;
        }

        .external__circle {
            width: 121px;
            height: 139px;
            border-radius: 330px;
            background: rgba(0, 87, 255, 0.17);
            filter: blur(100px);

            @media screen and (min-width: 768px) {
                width: 291px;
                height: 334px;
            }

            @media screen and (min-width: 1200px) {
                width: 287px;
                height: 330px;
            }
        }

        .internal__circle {
            left: 50%;
            transform: translateX(-50%);
            margin-top: 18px;
            width: 195px;
            height: 225px;
            fill: rgba(86, 144, 255, 0.13);
            filter: blur(75px);

            @media screen and (min-width: 768px) {
                width: 195px;
                height: 225px;
            }

            @media screen and (min-width: 1200px) {
                width: 193px;
                height: 222px;
            }
        }
    }

    .scale0 {
        transform: scale(0%);
    }


    &--active {

        .year,
        .title,
        .desc {
            color: #ECF1FF;
        }

        .year,
        .title {
            text-shadow: 0px 0px 4px rgba(227, 242, 255, 0.35);
        }
    }

    .grid-row1 {
        grid-row: 1;
        justify-self: auto;
        text-align: start;
        
        @media screen and (min-width: 961px) {
            justify-self: end;
            text-align: end;
        }
    }
}
</style>