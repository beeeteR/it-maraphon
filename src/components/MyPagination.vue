<template>
    <div class="pagination">
        <pagination-item v-for="page in store.pages" :key="page.id" :page="page"></pagination-item>
    </div>
</template>

<script>
import { useMainStore } from '@/stores/store'
import PaginationItem from './PaginationItem.vue';

export default {
    components: {
        PaginationItem
    },
    data() {
        return {
            store: useMainStore()
        }
    },
}
</script>

<style lang="scss">
.pagination {
    position: fixed;
    top: 50%;
    left: 60px;
    transform: translateY(-50%);
    display: none;
    flex-direction: column;
    gap: 24px;


    @media screen and (min-width: 961px) {
        display: flex;
    }

    @media screen and (max-height: 360px) {
        display: none;
    }
}
</style>