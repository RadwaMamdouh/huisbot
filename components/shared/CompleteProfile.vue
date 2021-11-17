<template>
  <v-dialog
    v-model="dialog"
    width="100%"
    content-class="complete_profile_dialog"
    overlay-color="#634DDC"
    overlay-opacity="0.70"
  >
    <v-card class="complete_profile_dialog--content">
      <img src="@/assets/img/complete-profile-bg.png" alt="" class="img_bg" />
      <div class="wrapper">
        <div class="head">
          <div class="title">Complete Profile</div>
          <v-btn text @click="dialog = false" class="close_btn">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </div>
        <div class="invite_more">
          <div class="left">
            <div class="invite_more--tit">Complete Your Profile</div>
            <div class="invite_more--desc">
              Your profile need to be completed to get properties information
              and
            </div>
          </div>
          <div class="right">
            <img src="@/assets/img/complete-profile.png" alt="" />
          </div>
        </div>
        <div class="dialog_actions">
          <v-btn class="not_now" text @click="dialog = false">Not Now</v-btn>
          <v-btn class="complete" text>Let’s Complete</v-btn>
        </div>
      </div>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "CompleteProfile",

  data() {
    return {
      dialog: false,
    };
  },
};
</script>

<style lang="scss">
.complete_profile_dialog {
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

  &--content {
    background-color: transparent !important;
    box-shadow: none !important;
    padding: 20px;

    @media (max-width: 600.98px) {
      padding: 0;
      margin: 0;
    }

    .img_bg {
      width: 100%;
      height: 100%;
      // max-height: 400px;

      @media (max-width: 600.98px) {
        margin: 0;
        height: 255px;
      }
    }

    .wrapper {
      position: absolute;
      z-index: 1;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      padding: 100px 100px 0;

      @media (max-width: 600.98px) {
        padding: 30px 35px;
      }
    }

    .head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 18px;

      .title {
        font-size: 24px;
        color: $purpleColor;
        font-family: bokraFontBold, sans-serif;
        font-weight: 700;
      }

      .close_btn {
        height: auto;
        min-width: auto;
        padding: 0;
        color: $purpleColor;

        .v-icon {
          color: $purpleColor;
          font-size: 24px;
        }
      }
    }

    .invite_more {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      column-gap: 87px;
      margin-bottom: 5px;

      @media (max-width: 600.98px) {
        column-gap: 10px;
        margin-bottom: 15px;
      }

      &--tit {
        font-size: 18px;
        color: #313131;
        font-family: bokraFontBold, sans-serif;
        font-weight: 700;
        margin-bottom: 13px;

        @media (max-width: 600.98px) {
          font-size: 16px;
        }
      }

      &--desc {
        font-size: 14px;
        color: #313131;

        @media (max-width: 600.98px) {
          font-size: 12px;
        }
      }

      .right {
        img {
          @media (max-width: 600.98px) {
            width: 100%;
            max-width: 120px;
          }
        }
      }
    }

    .dialog_actions {
      display: flex;
      align-items: center;
      justify-content: flex-start;
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
