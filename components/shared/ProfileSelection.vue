<template>
  <v-menu
    offset-y
    :contentClass="`profile_menu ${responsive ? 'responsive' : ''}`"
  >
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        v-bind="attrs"
        v-on="on"
        class="profile_selection"
        :class="`${withScroll ? 'withScroll' : ''} ${
          responsive ? 'd-block d-md-none' : 'd-none d-md-block'
        }`"
      >
        <div class="profile_img">
          <img src="@/assets/img/profile.png" alt="" />
        </div>
        <div class="name">Elean Ali</div>
        <v-icon>mdi-chevron-down</v-icon>
      </v-btn>
    </template>
    <v-list class="profile_selection_list">
      <v-list-item>
        <nuxt-link to="">
          <img src="@/assets/img/my-account.svg" alt="" />
          <span>My account</span>
        </nuxt-link>
      </v-list-item>
      <v-list-item>
        <nuxt-link to="">
          <img src="@/assets/img/logout.svg" alt="" />
          <span>Logout</span>
        </nuxt-link>
      </v-list-item>
    </v-list>
  </v-menu>
</template>

<script>
export default {
  name: "ProfileSelection",

  props: {
    withScroll: {
      type: Boolean,
    },
    responsive: {
      type: Boolean,
    },
  },

  data() {
    return {};
  },
};
</script>

<style lang="scss">
.profile_selection {
  &.v-btn {
    background-color: transparent !important;
    border-color: $purpleColor !important;
    box-shadow: none !important;
    height: auto !important;
    min-width: auto !important;
    padding: 0 !important;
    text-transform: capitalize !important;

    &::before {
      display: none;
    }

    &[aria-expanded="true"] {
      .v-icon {
        transform: rotate(180deg);
      }
    }

    .v-btn__content {
      display: flex;
      align-items: center;
      justify-content: center;
      column-gap: 10px;

      .profile_img {
        flex-shrink: 0;
        width: 24px;
        height: 24px;
        border: 1px solid #fff;
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
        }
      }

      .name {
        font-size: 14px;
        color: #fff;
        font-family: bokraFontMedium, sans-serif;
        font-weight: 500;
      }

      .v-icon {
        color: #fff;
        font-size: 24px;
      }
    }
  }

  &.withScroll {
    .v-btn__content {
      .profile_img {
        border-color: $purpleColor;
      }

      .name {
        color: $purpleColor;
      }

      .v-icon {
        color: $purpleColor;
      }
    }
  }
}

.profile_menu {
  box-shadow: none !important;

  .profile_selection_list {
    &.v-list {
      background-color: #9481ff;
      box-shadow: none !important;
      backdrop-filter: brightness(15) blur(30px) opacity(0);
      color: #fff;
      padding: 0;

      .v-list-item {
        padding: 0;
        width: 100%;
        min-height: auto !important;

        a {
          display: flex;
          align-items: center;
          justify-content: flex-start;
          column-gap: 5px;
          width: 100%;
          padding: 12px 15px;
          color: #fff;
          text-decoration: none;
          transition: 0.3s;

          img {
            flex-shrink: 0;
          }

          span {
            font-size: 15px;
            color: #fff;
          }

          &:hover {
            font-weight: 600;

            span {
              font-weight: 600;
            }
          }
        }
      }
    }
  }

  &.responsive {
    z-index: 999 !important;
  }
}
</style>
