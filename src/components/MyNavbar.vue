<template>
  <nav class="navbar" :class="{ 'nav-bg-collapse': stateCollapse }">
    <router-link to="/" class="logo"><img src="../assets/Logo.svg" alt="logo"></router-link>
    <div class="collapse" ref="collapse">
      <ul class="nav__items">
        <li class="nav__item"><router-link to="/" class="nav__link">О колледже</router-link></li>
        <li class="nav__item"><router-link to="/" class="nav__link">Абитуриентам</router-link></li>
        <li class="nav__item"><router-link to="/" class="nav__link">Студентам</router-link></li>
        <li class="nav__item"><router-link to="/" class="nav__link">Преподавателям</router-link></li>
        <li class="nav__item"><router-link to="/" class="nav__link">Трудоустройство</router-link></li>
        <li class="nav__item"><router-link to="/" class="nav__link">Автошкола</router-link></li>
      </ul>
      <div class="nav__icons">
        <div class="nav__icon">
          <img src="../assets/Search.svg" alt="search">
        </div>
        <div class="nav__icon">
          <img src="../assets/Visuallyimpaired.svg" alt="visibility">
        </div>
      </div>
    </div>
    <div class="collapse__btn" @click="changeStateCollapse()">
      <svg width="38" height="30" viewBox="0 0 38 30" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path ref="firstPath" d="M1.28125 28.3438H36.7188M1.28125" stroke="#6197FF" stroke-width="2"
          stroke-linecap="round" stroke-linejoin="round" />
        <path ref="secondPath" d="M1.28125 14.8438H36.7188M1.28125" stroke="#6197FF" stroke-width="2"
          stroke-linecap="round" stroke-linejoin="round" />
        <path ref="lastPath" d="M1.28125 1.34375H36.7188" stroke="#6197FF" stroke-width="2" stroke-linecap="round"
          stroke-linejoin="round" />
      </svg>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      stateCollapse: false,
    }
  },
  methods: {
    changeStateCollapse() {
      this.stateCollapse = !this.stateCollapse
      this.$refs.collapse.classList.toggle('collapsed')
    },
    changePath() {
      if (this.stateCollapse) {
        this.$refs.firstPath.style.transform = 'rotateZ(45deg) translate(4px, -31px)'
        this.$refs.secondPath.classList.add('to-left')
        this.$refs.lastPath.style.transform = 'rotateZ(-45deg) translate(-16px, 22px)'
      } else {
        this.$refs.firstPath.style.transform = 'translate(0px, 0px)'
        this.$refs.secondPath.classList.remove('to-left')
        this.$refs.lastPath.style.transform = 'translate(0px, 0px)'
      }
    }
  },
  watch: {
    stateCollapse() {
      this.changePath()
    }
  }
}
</script>

<style lang="scss">
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  align-items: center;
  padding: 11px 10px;
  background: rgba(17, 25, 56, 0.01);
  backdrop-filter: blur(3.5px);
  z-index: 100;
  transition: background-color 50ms 100ms;

  @media screen and (min-width: 576px) {
    padding: 11px 30px;
  }

  @media screen and (min-width: 768px) {
    padding: 15px 94px;
  }

  @media screen and (min-width: 961px) {
    padding: 15px 20px;
  }

  @media screen and (min-width: 1400px) {
    padding: 15px 65px;
  }

  .logo {
    min-width: 28px;
    transition: all 300ms;

    img {
      width: 100%;
    }

    @media screen and (min-width: 320px) {
      height: 28px;
      width: 48px;
    }

    @media screen and (min-width: 576px) {
      height: 48px;
      width: 88px;
    }

    @media screen and (min-width: 768px) {
      height: 60px;
      width: 104px;
    }

    &:hover {
      transform: scale(105%);
      filter: invert(43%) sepia(10%) saturate(2259%) hue-rotate(170deg) brightness(85%) contrast(81%);
    }

    &:active {
      transition: all 50ms;
      transform: scale(90%);
      filter: none;
    }
  }

  .collapse {
    display: flex;
    justify-content: center;
    position: absolute;
    padding: 75px 99px 0;
    top: 54px;
    height: 100vh;
    transform: translateY(-300%);
    background: #121B3E;
    left: 0;
    margin-left: 0;
    width: 100%;
    overflow: hidden;
    z-index: -1;
    transition: all 500ms;

    @media screen and (min-width: 768px) {
      justify-content: flex-start;
    }

    @media screen and (min-width: 961px) {
      position: static;
      height: auto;
      transform: unset;
      padding: unset;
      background: unset;
      margin-left: 1em;
    }

    @media screen and (min-width: 1200px) {
      margin-left: 2em;
    }

    @media screen and (min-width: 1400px) {
      margin-left: 4em;
    }

    @media screen and (min-width: 1500px) {
      margin-left: 87px;
    }

    .nav__items {
      display: flex;
      flex-direction: column;
      gap: 42px 100%;
      max-height: 222px;
      list-style: none;
      transition: all 400ms;
      
      @media screen and (min-width: 768px) {
        flex-wrap: wrap;
      }

      @media screen and (min-width: 961px) {
        gap: 1em;
        flex-direction: row;
        flex-wrap: nowrap;
      }

      @media screen and (min-width: 1200px) {
        gap: 2em;
      }

      @media screen and (min-width: 1400px) {
        gap: 3em;
      }

      @media screen and (min-width: 1500px) {
        gap: 4em;
      }



      .nav__item {
        width: fit-content;

        .nav__link {
          text-decoration: none;
          font-size: 16px;
          font-weight: 600;
          transition: all 300ms;

          @media screen and (min-width: 1200px) {
            font-size: 16px;
          }

          @media screen and (min-width: 1400px) {
            font-size: 18px;
          }

          &:hover {
            text-decoration: underline;
            opacity: 0.7;
          }
        }
      }
    }

    .nav__icons {
      display: none;
      margin-left: auto;
      gap: 35px;

      @media screen and (min-width: 961px) {
        display: flex;
      }

      .nav__icon {
        cursor: pointer;
        transition: all 300ms;

        &:hover {
          transform: scale(115%);
        }

        &:active {
          transition: all 50ms;
          transform: scale(85%);
        }
      }
    }
  }

  .collapsed {
    transform: translateY(0);
  }

  .collapse__btn {
    display: block;
    width: 32px;
    height: 32px;
    margin-left: auto;
    cursor: pointer;

    @media screen and (min-width: 576px) {
      width: auto;
      height: auto;
    }

    @media screen and (min-width: 961px) {
      display: none;
    }

    svg {
      width: 100%;

      path {
        transition: all 300ms;
      }
    }

  }
}

.nav-bg-collapse {
  background-color: #121B3E;
}

.to-left {
  transform: translateX(-150%);
}
</style>