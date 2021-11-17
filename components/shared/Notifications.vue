<template>
  <v-menu offset-y :left="true" contentClass="notifications_menu">
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        v-bind="attrs"
        v-on="on"
        class="notifications_selection"
        :class="{ withScroll: withScroll }"
      >
        <img src="@/assets/img/notifications.svg" alt="" />
      </v-btn>
    </template>
    <v-list class="notifications_selection_list">
      <div class="title">My account</div>
      <div class="notifications_rows">
        <div class="notification_row">
          <div class="tit_time">
            <div class="tit">Email For You</div>
            <div class="time">01:00 PM</div>
          </div>
          <div class="desc">
            New property matches your requirements had been added
          </div>
        </div>
        <div class="notification_row">
          <div class="tit_time">
            <div class="tit">Email For You</div>
            <div class="time">01:00 PM</div>
          </div>
          <div class="desc">
            New property matches your requirements had been added
          </div>
        </div>
        <div class="notification_row">
          <div class="tit_time">
            <div class="tit">Email For You</div>
            <div class="time">01:00 PM</div>
          </div>
          <div class="desc">
            New property matches your requirements had been added
          </div>
        </div>
      </div>
      <nuxt-link to="" class="show_more">
        <span>Show More</span>
        <v-icon>mdi-chevron-down</v-icon>
      </nuxt-link>
    </v-list>
  </v-menu>
</template>

<script>
export default {
  name: "Notifications",

  props: {
    withScroll: {
      type: Boolean,
    },
  },
};
</script>

<style lang="scss">
.notifications_selection {
  &.v-btn {
    padding: 5px !important;
    background-color: #5945c6 !important;
    border-radius: 2px;
    border-color: $purpleColor !important;
    box-shadow: none !important;
    height: auto !important;
    min-width: auto !important;
    backdrop-filter: brightness(3) blur(10px) opacity(0);

    &::before {
      display: none;
    }
  }

  // &.withScroll {
  //   .v-btn__content {
  //   }
  // }
}

.notifications_menu {
  box-shadow: none !important;
  overflow-y: hidden !important;
  max-width: 25% !important;

  .notifications_selection_list {
    padding: 0 !important;
    &.v-list {
      background-color: #9481ff;
      box-shadow: none !important;
      backdrop-filter: brightness(15) blur(30px) opacity(0);

      .title {
        font-size: 14px;
        color: #fff;
        font-family: bokraFontMedium, sans-serif;
        font-weight: 500;
        margin-bottom: 16px;
        padding: 10px 20px 0;
      }

      .notifications_rows {
        padding: 0 20px 20px;
        overflow-x: hidden;
        overflow-y: auto;
        max-height: 300px;

        .notification_row {
          &:not(:last-child) {
            border-bottom: 1px solid rgba(#f9f9f9, 0.2);
            padding-bottom: 20px;
            margin-bottom: 20px;
          }

          .tit_time {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 8px;

            .tit {
              font-size: 11px;
              color: #111111;
              font-family: bokraFontMedium, sans-serif;
              font-weight: 500;
            }

            .time {
              font-size: 11px;
              color: #111111;
              font-family: bokraFontMedium, sans-serif;
              font-weight: 500;
            }
          }

          .desc {
            font-size: 12px;
            color: #eaeaea;
          }
        }
      }

      .show_more {
        display: flex;
        align-items: center;
        justify-content: center;
        column-gap: 5px;
        width: 100%;
        padding: 10px;
        text-decoration: none;
        background-color: #a08fff;
        backdrop-filter: brightness(3) blur(10px) opacity(0);
        color: $purpleColor;
        transition: 0.3s;

        span {
          color: $purpleColor;
          font-size: 12px;
        }

        .v-icon {
          color: $purpleColor;
          font-size: 24px;
        }

        &:hover {
          span {
            font-weight: 600;
          }

          .v-icon {
            #{$ltr} & {
              transform: rotate(-90deg);
            }
            #{$rtl} & {
              transform: rotate(90deg);
            }
          }
        }
      }
    }
  }
}
</style>
