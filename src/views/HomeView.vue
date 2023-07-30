<template>
  <my-pagination></my-pagination>
  <div class="container">
    <div class="toc">
      <h1 class="organization__name">
        ОГАПОУ «УАвиаК-МЦК»
      </h1>
      <p class="organization__desc">
        Областное государственное автономное профессиональное образовательное учреждение «Ульяновский авиационный колледж
        —
        Межрегиональный центр компетенций»
      </p>
    </div>
    <history-item v-for="page in store.pages" :key="page.id" :page="page" ref="page" :id="page.id"></history-item>
  </div>
</template>

<script>
import { useMainStore } from '@/stores/store'
import MyPagination from '@/components/MyPagination.vue'
import HistoryItem from '@/components/HistoryItem.vue'

export default {
  name: 'HomeView',
  components: {
    MyPagination,
    HistoryItem
  },
  data() {
    return {
      store: useMainStore(),
      pagesRef: []
    }
  },
  mounted() {
    window.addEventListener('scroll', () => {
      this.checkActivePage()
    })
  },
  methods: {
    checkActivePage() {
      this.$refs.page.forEach(el => {
        let elRect = el.$el.getBoundingClientRect()
        let elPosY = elRect.y
        let elHeight = elRect.height
        const windowHeight = window.innerHeight
        if (elPosY + elHeight / 2 <= windowHeight / 2 + 200 && elPosY - elHeight / 2 >= windowHeight / 2 - 350) {
          this.store.changeCurrentPage(Number(el.$el.id))
        }
      })
    }
  }
}
</script>
<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  margin-bottom: 175px;

  .toc {
    max-width: 810px;
    margin-bottom: 90px;

    @media screen and (min-width: 320px) {
      margin-bottom: 39px;
    }

    @media screen and (min-width: 768px) {
      margin-bottom: 125px;
    }

    @media screen and (min-width: 1200px) {
      margin-top: 90px;
    }


    .organization__name {
      font-size: 72px;
      font-weight: 400;
      line-height: 115%;

      @media screen and (min-width: 320px) {
        font-size: 20px;
        line-height: 135%;
      }

      @media screen and (min-width: 576px) {
        font-size: 36px;
      }

      @media screen and (min-width: 768px) {
        font-size: 54px;
      }

      @media screen and (min-width: 1200px) {
        font-size: 72px;
      }
    }

    .organization__desc {
      margin-top: 12px;
      font-size: 14px;
      font-weight: 400;

      @media screen and (min-width: 320px) {
        font-size: 14px;
        line-height: 155%;
      }
      @media screen and (min-width: 576px) {
        font-size: 16px;
      }

      @media screen and (min-width: 768px) {
        line-height: 155%;
        font-size: 24px;
      }

      @media screen and (min-width: 1200px) {
        line-height: 150%;
      }
    }
  }
}
</style>