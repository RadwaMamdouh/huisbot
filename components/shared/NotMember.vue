<template>
  <v-dialog
    v-model="dialog"
    width="100%"
    content-class="not_member_dialog"
    overlay-color="#634DDC"
    overlay-opacity="0.70"
  >
    <v-card class="not_member_dialog--content">
      <img src="@/assets/img/not-member-bg.png" alt="" class="img_bg" />
      <div class="wrapper">
        <div class="head">
          <div class="img">
            <img src="@/assets/img/not-member.png" alt="" />
          </div>
          <v-btn text @click="dialog = false" class="close_btn">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </div>
        <div class="invite_more">
          <div class="left">
            <div class="invite_more--tit">
              Oh! It Seems That You Aren’t Member
            </div>
            <div class="invite_more--desc">
              You can easily subscribe and be one of best members
            </div>
          </div>
        </div>
        <div class="dialog_actions">
          <v-btn class="not_now" text @click="dialog = false">Not Now</v-btn>
          <v-btn class="complete" text>Subscribe</v-btn>
        </div>
      </div>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "NotMember",

  data() {
    return {
      dialog: false,
    };
  },
};
</script>

<style lang="scss">
.not_member_dialog {
  max-width: 50%;
  box-shadow: none !important;

  @media (max-width: 1400.98px) {
    max-width: 55%;
  }

  @media (max-width: 1264.98px) {
    max-width: 75%;
  }

  @media (max-width: 960.98px) {
    max-width: 95%;
  }

  @media (max-width: 600.98px) {
    margin: 0;
  }

  &--content {
    background-color: transparent !important;
    box-shadow: none !important;
    position: relative;

    @media (max-width: 600.98px) {
      padding: 0;
    }

    .img_bg {
      width: 100%;
      height: 100%;
      max-height: 400px;

      @media (max-width: 600.98px) {
        margin: 0;
        height: 330px;
      }
    }

    .wrapper {
      position: absolute;
      z-index: 1;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    .head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 18px;
      padding: 0 80px;
      //   position: relative;

      .img {
        margin: 0 auto;

        img {
          @media (max-width: 600.98px) {
            max-width: 120px;
          }
        }
      }

      .close_btn {
        height: auto;
        min-width: auto;
        padding: 0;
        color: $purpleColor;
        // position: absolute;
        // top: 35%;
        // #{$ltr} & {
        //   right: 5%;
        // }
        // #{$rtl} & {
        //   left: 5%;
        // }

        .v-icon {
          color: $purpleColor;
          font-size: 24px;
        }
      }
    }

    .invite_more {
      display: flex;
      align-items: center;
      justify-content: center;

      &--tit {
        font-size: 18px;
        color: #313131;
        font-family: bokraFontBold, sans-serif;
        font-weight: 700;
        margin-bottom: 10px;

        @media (max-width: 600.98px) {
          font-size: 16px;
        }
      }

      &--desc {
        font-size: 14px;
        color: #313131;
        margin-bottom: 16px;

        @media (max-width: 600.98px) {
          font-size: 12px;
        }
      }
    }

    .dialog_actions {
      display: flex;
      align-items: center;
      justify-content: center;
      column-gap: 16px;

      .v-btn {
        @extend %btn;
        padding: 10px 14px !important;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 5px;

        &.not_now {
          @include buttonStyle(#fff, $purpleColor, transparent);

          .v-btn__content {
            font-size: 14px;
            text-transform: capitalize;
          }
        }

        &.complete {
          @include buttonStyle($purpleColor, #fff, $purpleColor);

          .v-btn__content {
            font-size: 14px;
            text-transform: capitalize;
          }
        }
      }
    }
  }
}
</style>
