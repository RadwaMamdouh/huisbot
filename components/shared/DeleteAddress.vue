<template>
  <v-dialog
    v-model="dialog"
    width="100%"
    content-class="delete_address_dialog"
    overlay-color="#634DDC"
    overlay-opacity="0.70"
  >
    <v-card class="delete_address_dialog--content">
      <img src="@/assets/img/not-member-bg.png" alt="" class="img_bg" />
      <div class="wrapper">
        <div class="head">
          <div class="img">
            <img src="@/assets/img/delete-address.png" alt="" />
          </div>
          <v-btn text @click="dialog = false" class="close_btn">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </div>
        <div class="invite_more">
          <div class="left">
            <div class="invite_more--tit">Delete Address</div>
            <div class="invite_more--desc">
              Are you sure you want to delete your address once you delete it
              will be lost it’s information.
            </div>
          </div>
        </div>
        <div class="dialog_actions">
          <v-btn class="not_now" text @click="dialog = false">Cancel</v-btn>
          <v-btn class="complete" text>Delete</v-btn>
        </div>
      </div>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "DeleteAddress",

  props: {
    openDialog: {
      type: Boolean,
      required: true,
    },
  },

  computed: {
    dialog: {
      get() {
        return this.openDialog;
      },

      set(value) {
        this.$emit("clicked", value);
      },
    },
  },
};
</script>

<style lang="scss">
.delete_address_dialog {
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
      max-height: 443px;

      @media (max-width: 600.98px) {
        margin: 0;
        height: 280px;
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
        font-size: 24px;
        color: $purpleColor;
        font-family: bokraFontBold, sans-serif;
        font-weight: 700;
        margin-bottom: 10px;
        text-align: center;

        @media (max-width: 600.98px) {
          font-size: 16px;
        }
      }

      &--desc {
        font-size: 14px;
        color: #313131;
        max-width: 70%;
        margin: 0 auto 16px;
        text-align: center;

        @media (max-width: 600.98px) {
          font-size: 12px;
        }
      }
    }

    .dialog_actions {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      column-gap: 16px;
      padding: 0 80px;

      .v-btn {
        @extend %btn;
        padding: 8px 18px !important;
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
