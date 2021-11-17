<template>
  <div class="invite_freinds">
    <v-dialog
      v-model="dialog"
      width="100%"
      content-class="invite_freinds_dialog"
      overlay-color="#634DDC"
      overlay-opacity="0.70"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="invite_freinds_button">
          Invite Friends
        </v-btn>
      </template>

      <v-card class="invite_freinds_dialog--content">
        <img src="@/assets/img/invite-freinds-bg.png" alt="" class="img_bg" />
        <div class="wrapper">
          <div class="head">
            <div class="title">Invite Friends</div>
            <v-btn text @click="dialog = false" class="close_btn">
              <v-icon>mdi-close</v-icon>
            </v-btn>
          </div>
          <div class="invite_more">
            <div class="left">
              <div class="invite_more--tit">Let’s Invite More Users</div>
              <div class="invite_more--desc">
                Your can easily invite more friends to get points
              </div>
            </div>
            <div class="right">
              <img src="@/assets/img/invite-firends.png" alt="" />
            </div>
          </div>
          <div class="link_invitation">
            <div class="link_invitation--tit">Link of invitation</div>
            <div class="link_invitation--input">
              <v-text-field
                label="Link of Invitation"
                placeholder="https://dribbble.com/shots/15341571-Sisyphus-dashboard-profile-settings"
                value="https://dribbble.com/shots/15341571-Sisyphus-dashboard-profile-settings"
                hide-details
                readonly
                solo
              ></v-text-field>
              <v-btn text class="copy_btn">
                <v-icon>mdi-content-copy</v-icon>
              </v-btn>
            </div>
          </div>
        </div>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: "InviteFreinds",

  data() {
    return {
      dialog: false,
    };
  },
};
</script>

<style lang="scss">
.invite_freinds {
  &_button {
    &.v-btn {
      padding: 4px 6px !important;
      background-color: transparent !important;
      border-radius: 2px;
      box-shadow: none !important;
      height: auto !important;
      min-width: auto !important;
      text-transform: capitalize !important;
      border: 1px solid transparent;

      &::before {
        display: none;
      }

      .v-btn__content {
        color: $greenColor;
        font-size: 12px;
        font-family: bokraFontMedium, sans-serif;
        font-weight: 500;
      }

      &:hover {
        border-color: $greenColor !important;
      }
    }
  }
}

.invite_freinds_dialog {
  max-width: 50%;
  box-shadow: none !important;

  @media (max-width: 1400.98px) {
    max-width: 60%;
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
    // padding: 100px 75px;

    @media (max-width: 600.98px) {
      padding: 0;
    }

    .img_bg {
      width: 100%;
      height: 100%;
      // max-height: 400px;

      @media (max-width: 600.98px) {
        margin: 0;
        height: 380px;
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
        padding: 40px 45px;
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
          @media (max-width: 960.98px) {
            width: 100%;
          }

          @media (max-width: 600.98px) {
            max-width: 120px;
          }
        }
      }
    }

    .link_invitation {
      &--tit {
        font-size: 15px;
        color: $purpleColor;
        font-weight: 600;
        margin-bottom: 8px;
      }

      &--input {
        background-color: #fff;
        border-radius: 8px;
        display: flex;
        align-items: center;
        overflow: hidden;

        .v-input {
          font-size: 12px;
          color: #626366;

          &__control {
            min-height: auto;
          }

          &__slot {
            padding: 16px !important;
            box-shadow: none !important;

            .v-label {
              font-size: 12px;
            }

            input {
              padding: 0 !important;
            }
          }
        }

        .copy_btn {
          &.v-btn {
            height: auto !important;
            min-width: auto !important;
            padding: 16px !important;
            color: $purpleColor;

            .v-btn__content {
              .v-icon {
                color: $purpleColor;
                font-size: 20px;
              }
            }
          }
        }
      }
    }
  }
}
</style>
