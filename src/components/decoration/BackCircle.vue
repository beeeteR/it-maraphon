<template>
    <div class="back__circle" :class="{ 'up': up }"></div>
</template>

<script>
export default {
    props: {
        up: {
            type: Boolean,
            default: false
        }
    }
}
</script>

<style lang="scss" scoped>
.back__circle {
    position: fixed;
    top: auto;
    left: auto;
    bottom: -20%;
    right: -10%;
    width: 276px;
    height: 286px;
    border-radius: 100%;
    background: rgba(0, 87, 255, 0.15);
    filter: blur(175px);

    @media screen and (min-width: 768px) {
        width: 600px;
        height: 600px;
    }

    @media screen and (min-width: 1200px) {
        width: 756px;
        height: 784px;
    }
}

.up {
    bottom: auto;
    right: auto;
    left: 8%;
    top: -30%;
    background: rgba(0, 87, 255, 0.08);
}
</style>