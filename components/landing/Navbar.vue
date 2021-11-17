<template>
  <div class="app_header_holder_landing" :class="{ onScroll: !view.topOfPage }">
    <v-container>
      <header class="app_header">
        <div class="app_header--left">
          <nuxt-link to="/" class="logo">
            <img
              v-if="view.topOfPage"
              src="@/assets/img/Huisbot-white.png"
              alt=""
            />
            <img v-if="!view.topOfPage" src="@/assets/img/Huisbot.png" alt="" />
          </nuxt-link>
          <div class="menu_links d-none d-md-flex">
            <nuxt-link to="/">
              <span>Home</span>
            </nuxt-link>
            <nuxt-link to="/about">
              <span>About us</span>
            </nuxt-link>
            <nuxt-link to="/contact">
              <span>Contact us</span>
            </nuxt-link>
          </div>
        </div>
        <div class="app_header--right">
          <v-btn to="/auth/login" class="btnStyle loginBtn d-none d-md-flex">
            Login
          </v-btn>
          <v-btn
            to="/auth/register"
            class="btnStyle registerBtn d-none d-md-flex"
          >
            Register
          </v-btn>
          <!-- Language Selection -->
          <LangSelection :landing="true" :with-scroll="!view.topOfPage" />
          <!-- Icon to open menu in responsive -->
          <v-app-bar-nav-icon
            class="d-block d-md-none"
            @click="drawer = true"
          ></v-app-bar-nav-icon>
        </div>
      </header>
    </v-container>

    <!-- Menu in responsive -->
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <v-btn class="close_Menu" @click="drawer = false">
        <v-icon>mdi-close</v-icon>
      </v-btn>
      <v-list nav dense>
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-title>
              <nuxt-link to="/">Home</nuxt-link>
            </v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>
              <nuxt-link to="/about">About us</nuxt-link>
            </v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>
              <nuxt-link to="/contact">Contact us</nuxt-link>
            </v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
      <div class="menu_btns">
        <v-btn to="/login" class="btnStyle loginBtn">Login</v-btn>
        <v-btn to="/register" class="btnStyle registerBtn">Register</v-btn>
      </div>
    </v-navigation-drawer>
  </div>
</template>

<script>
import LangSelection from "@/components/shared/LangSelection";

export default {
  name: "Navbar",

  components: {
    LangSelection,
  },

  data() {
    return {
      view: {
        topOfPage: true,
      },
      drawer: false,
      group: null,
    };
  },

  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },

  methods: {
    handleScroll() {
      if (window.pageYOffset > 0) {
        if (this.view.topOfPage) this.view.topOfPage = false;
      } else if (!this.view.topOfPage) {
        this.view.topOfPage = true;
      }
    },
  },
};
</script>

<style lang="scss">
.app_header_holder_landing {
  background-color: transparent;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 999;
  transition: 0.3s;

  .app_header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    &--left {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      column-gap: 35px;

      .logo {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 28px;
        flex-shrink: 0;

        img {
          width: 100%;
          height: 100%;
        }
      }

      .menu_links {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        column-gap: 24px;

        a {
          text-decoration: none;
          font-size: 14px;
          font-weight: 500;
          font-family: bokraFontMedium, sans-serif;
          color: #fff;
          padding: 10px;
          position: relative;
          transition: 0.3s;

          &::before {
            content: "";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 100%;
            background-color: #fff;
            height: 0;
            opacity: 0;
            visibility: hidden;
            transition: 0.3s;
          }

          &:hover,
          &.nuxt-link-exact-active {
            color: #634ddc;

            &::before {
              height: 100%;
              opacity: 1;
              visibility: visible;
            }

            span {
              position: relative;
              z-index: 1;
            }
          }

          span {
            font-family: bokraFontMedium, sans-serif;
          }
        }
      }
    }

    &--right {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      column-gap: 16px;

      .loginBtn {
        @include buttonStyle(#fff, $purpleColor, $purpleColor);
        padding: 10px 20px;
        text-transform: capitalize;
      }

      .registerBtn {
        @include buttonStyle($greenColor, #fff, transparent);
        padding: 10px 20px;
        text-transform: capitalize;
      }
    }
  }

  &.onScroll {
    background-color: rgba(255, 255, 255, 0.98);
    box-shadow: 0 2px 20px rgba(#634ddc, 0.2);
    backdrop-filter: brightness(10) blur(10px) opacity(0);

    .menu_links {
      a {
        color: #634ddc;

        &::before {
          background-color: #634ddc;
        }

        &:hover,
        &.nuxt-link-exact-active {
          color: #fff;
        }
      }
    }
  }
}

.v-app-bar__nav-icon {
  background-color: $purpleColor;
  color: #fff !important;

  .v-btn__content {
    color: #fff !important;
  }
}

.v-overlay {
  &--absolute {
    min-height: 100vh;
  }
}

.v-navigation-drawer {
  background-color: $purpleColor !important;
  min-height: 100vh;

  #{$rtl} & {
    left: auto !important;
    right: 0 !important;
  }

  &.v-navigation-drawer--close {
    #{$rtl} & {
      transform: translateX(100%) !important;
    }
  }

  .close_Menu {
    display: flex;
    margin-inline-start: auto;
    margin-inline-end: 5px;
    margin-top: 5px;
    border-radius: 100%;
    min-width: unset !important;
    width: 36px;
    color: $purpleColor;
  }

  .v-list {
    margin: 10px 0;

    &-item {
      color: #fff !important;
      min-height: auto !important;
      padding: 0 !important;

      &--active {
        &::before {
          opacity: 0 !important;
        }
      }

      &__title {
        width: 100%;
        height: 100%;

        a {
          color: #fff !important;
          text-decoration: none;
          font-size: 16px;
          font-weight: 500;
          font-family: bokraFontMedium, sans-serif;
          display: flex;
          justify-content: center;
          text-align: center;
          width: 100%;
          height: 100%;
          padding: 14px 8px;

          &.nuxt-link-exact-active {
            background-color: rgba(54, 29, 189, 0.29);
          }

          span {
            font-family: bokraFontMedium, sans-serif;
          }
        }
      }
    }
  }

  .menu_btns {
    display: flex;
    flex-direction: column;
    row-gap: 20px;

    .loginBtn {
      @include buttonStyle(#fff, $purpleColor, $purpleColor);
      padding: 10px 20px;
      text-transform: capitalize;
      width: 100%;
      max-width: 70%;
      margin: 0 auto;
    }

    .registerBtn {
      @include buttonStyle($greenColor, #fff, transparent);
      padding: 10px 20px;
      text-transform: capitalize;
      width: 100%;
      max-width: 70%;
      margin: 0 auto;
    }
  }
}
</style>
