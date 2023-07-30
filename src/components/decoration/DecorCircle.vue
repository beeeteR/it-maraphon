<template>
    <div class="decor__circle" :class="[boolDirection ? 'vert__circle' : 'hor__circle', { 'active__circle': isActive }]">
    </div>
</template>

<script>
export default {
    props: {
        isActive: {
            type: Boolean,
            default: false
        },
        direction: {
            type: String,
            default: 'vert'
        }
    },
    computed: {
        boolDirection() {
            if (this.direction == 'vert') {
                return true
            }
            return false
        }
    }
}
</script>

<style lang="scss">
.decor__circle {
    border-radius: 50%;
    background-color: #7190FF;
    filter: drop-shadow(0px 0px 19px #3562FF);
    transition: all 400ms;
}

.vert__circle {
    height: 11px;
    width: 11px;

    @media screen and (min-width: 768px) {
        width: 16px;
        height: 16px;
    }
}

.hor__circle {
    height: 8px !important;
    width: 8px !important;
    background-color: #7190FF !important;

    @media screen and (min-width: 768px) {
        width: 11px !important;
        height: 11px !important;
    }
}

.active__circle {
    width: 14px;
    height: 14px;
    background-color: #E3F2FF;

    @media screen and (min-width: 768px) {
        width: 24px;
        height: 24px;
    }
}
</style>