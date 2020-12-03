<template>
  <nav class="nav" :class="{ nav__scroll: scrollPosition > 50 }">
    <div class="nav__container">
      <div class="nav__logo">
        <h1>LOGO</h1>
      </div>
      <!-- Only visible when viewing with mobile device. -->
      <div class="nav__toggle" @click="menuOpened = !menuOpened">
        <div
          v-bind:class="{ nav__clicked: menuOpened }"
          class="nav__toggle-bar"
        ></div>
      </div>
      <!-- Only visible when viewing with iPad Pro and Desktop. -->
      <div class="nav__links">
        <nuxt-link to="/about" class="nav__links-item nav__links-item--home"
          >Home</nuxt-link
        >
        <nuxt-link to="/about" class="nav__links-item">About</nuxt-link>
        <nuxt-link to="/about" class="nav__links-item">Orthotics</nuxt-link>
        <nuxt-link to="/about" class="nav__links-item">Contact</nuxt-link>
      </div>
    </div>
    <div v-show="menuOpened" class="nav__menu">
      <nuxt-link to="/" class="nav__menu-item">Home</nuxt-link>
      <nuxt-link to="/about" class="nav__menu-item">About</nuxt-link>
      <nuxt-link to="/home" class="nav__menu-item">Orthotics</nuxt-link>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      menuOpened: false,
      scrollPosition: null
    };
  },
  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },
  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY;
    }
  }
};
</script>

<style lang="scss">
.nav {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  background: white;
  padding: 0 5%;
  &__scroll {
    box-shadow: 0 -0.5rem 1.5rem #212121;
    background: rgba(255, 255, 255, 0.9);
  }
  &__container {
    padding: 1.5rem 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
  }
  &__logo {
    &-img {
      height: 4rem;
    }
  }
  &__toggle {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 3.5rem;
    height: 3.5rem;
    background: #0088cc;
    border-radius: 0.25rem;
    cursor: pointer;
    &-bar,
    &-bar::before,
    &-bar::after {
      width: 1.7rem;
      height: 0.2rem;
      background: white;
      transition: all 0.5s ease-in-out;
    }
    &-bar::before,
    &-bar::after {
      content: "";
      position: absolute;
    }
    &-bar::before {
      transform: translateY(-0.5rem);
    }
    &-bar::after {
      transform: translateY(0.5rem);
    }
  }

  //Transform bars to an "X"
  &__clicked {
    transform: translateX(-0.4rem);
    background: transparent;
    &::before {
      transform: rotate(45deg) translate(0.3rem, -0.3rem);
    }
    &::after {
      transform: rotate(-45deg) translate(0.3rem, 0.3rem);
    }
  }

  //Navigation menu that opens when hamburger button is clicked
  &__menu {
    z-index: 9999;
    width: 100%;
    display: flex;
    flex-direction: column;
    padding: 0 2rem;
    position: relative;
    left: 0;
    bottom: 0;
    background: white;
    margin: 1.5rem 0;
    &-item {
      font-size: 1.4rem;
      text-transform: uppercase;
      font-weight: 700;
      padding: 1rem;
      color: #0088cc;
      &:not(:last-child) {
        border-bottom: 0.1rem solid #e8e8e8;
      }
      &-hover {
        background: #0088cc;
        color: white;
      }
    }
  }
  &__links {
    display: none;
  }
}
//Desktop View
@media (min-width: 1248px) {
  .nav {
    &__toggle {
      display: none;
    }
    //Navigation while viewing with bigger screens
    &__links {
      display: flex;
      font-size: 1.8rem;
      font-weight: 700;
      &-item {
        margin: 0 1.5rem;
        text-transform: uppercase;
        &--home,
        &:hover {
          color: #0088cc;
        }
      }
    }
  }
}
</style>
