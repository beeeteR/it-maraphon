<template>
    <div class="pagination__item" @click="changeCurrentPage()">
        <div class="pin" :class="{ 'pin__active': currPage == page.id }"></div>
    </div>
</template>

<script>
import { useMainStore } from '@/stores/store'
export default {
    props: {
        page: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            store: useMainStore(),
        }
    },
    methods: {
        changeCurrentPage() {
            document.getElementById(`${this.page.id}`).scrollIntoView({
                behavior: 'smooth', 
                inline: 'center',
                block: 'center'
            })
        }
    },
    computed: {
        currPage() {
            return this.store.getCurrentPage
        }
    }
}
</script>

<style lang="scss">
.pagination__item {
    width: 24px;
    height: 24px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;

    .pin {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background-color: #314373;
        outline: 0px solid #1849A0;
        transition: all 300ms;
    }

    .pin__active {
        background-color: #FCFDFD;
        outline: 6px solid #1849A0;

    }
}
</style>