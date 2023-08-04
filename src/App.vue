<template>
  <my-navbar></my-navbar>
  <router-view class="pages" />
  <div class="back__circles">
    <back-circle :up="true"></back-circle>
    <back-circle></back-circle>
  </div>
</template>

<script>
import BackCircle from './components/decoration/BackCircle.vue';
import MyNavbar from './components/MyNavbar.vue';

export default {
  components: {
    MyNavbar,
    BackCircle
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@200;300;400;500;600;700;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Manrope', sans-serif;
  color: white;
}

body {
  background: radial-gradient(50% 50.00% at 50% 50.00%, rgba(18, 27, 62, 0.00) 0%, rgba(8, 12, 21, 0.50) 100%), linear-gradient(0deg, #121B3E 0%, #121B3E 100%), #FFF;
}

.pages {
  position: fixed;
  width: 100%;
  height: 100%;
  overflow-y: auto;
}

.back__circles {
  position: relative;
  z-index: -1;
}

.container {
  margin: 86px 10px 0px;

  @media screen and (min-width: 576px) {
    margin: 160px 30px 0px;
  }

  @media screen and (min-width: 768px) {
    margin: 160px 90px 0px;
  }

  @media screen and (min-width: 960px) {
    margin: 160px 120px 0px;
  }

  @media screen and (min-width: 1400px) {
    margin: 90px 212px 0px;
  }
}
</style>
