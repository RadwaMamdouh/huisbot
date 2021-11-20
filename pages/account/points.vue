<template>
  <div class="my_points">
    <div class="top">
      <v-row>
        <v-col cols="12" lg="7">
          <h2>My Points</h2>
          <!-- Points List -->
          <div class="get_points">
            <h4>Le’s Get Points</h4>
            <ul class="get_points--list">
              <li>
                <v-icon>mdi-check</v-icon>
                <span>New web applications with a modern .</span>
              </li>
              <li>
                <v-icon>mdi-check</v-icon>
                <span>New web applications with a modern .</span>
              </li>
              <li>
                <v-icon>mdi-check</v-icon>
                <span>New web applications with a modern .</span>
              </li>
              <li>
                <v-icon>mdi-check</v-icon>
                <span>New web applications with a modern .</span>
              </li>
            </ul>
          </div>
          <!-- Charged Points -->
          <!-- <div class="charged_points">
            <h4>100 POINTS</h4>
            <h5>Charged to your account</h5>
          </div> -->
        </v-col>
        <v-col cols="12" lg="5">
          <img src="@/assets/img/my-points.png" alt="" class="my_points--img" />
        </v-col>
      </v-row>
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

    <div class="points_boxes">
      <v-row>
        <v-col cols="12" lg="6">
          <div class="points_box">
            <div class="points_box--tit">HOW TO EARN POINTS</div>
            <div class="points_box--desc">
              Every Time You Invite Friends You Will Earn Points Based On The
              Number Of Invites You Send.
            </div>
            <div class="points_box--rows">
              <div class="box-row">
                <span>No. Invitation</span>
                <span>Points</span>
              </div>
              <div class="box-row">
                <span>10 Invitation</span>
                <span>5 Point</span>
              </div>
            </div>
          </div>
        </v-col>
        <v-col cols="12" lg="6">
          <div class="points_box">
            <div class="points_box--tit">HOW TO SPEND POINTS</div>
            <div class="points_box--desc">
              Use Points In Your Coming Reservation As Discount For Your Future
              Connection At Our Website.
            </div>
            <div class="points_box--rows">
              <div class="box-row">
                <span>Points</span>
                <span>Redeemed For</span>
              </div>
              <div class="box-row">
                <span>5 pints</span>
                <span>1$</span>
              </div>
            </div>
          </div>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
export default {
  name: "points",
  layout: "loggedLayout",
};
</script>

<style lang="scss">
.my_points {
  h2 {
    font-size: 25px;
    color: #111111;
    font-family: bokraFontMedium, sans-serif;
    margin-bottom: 32px;
    font-weight: 500;
  }

  .top {
    margin-bottom: 45px;
  }

  &--img {
    width: 100%;
  }

  .get_points {
    h4 {
      font-size: 29px;
      color: $greenColor;
      font-family: bokraFontMedium, sans-serif;
      margin-bottom: 14px;
      font-weight: 500;
    }

    &--list {
      list-style: none;
      padding: 0;

      li {
        &:not(:last-child) {
          margin-bottom: 24px;
        }

        display: flex;
        align-items: flex-start;
        justify-content: flex-start;
        column-gap: 14px;

        .v-icon {
          width: 36px;
          height: 36px;
          border-radius: 100%;
          background-color: $purpleColor;
          border: 5px solid #bfb3ff;
          display: flex;
          align-items: center;
          justify-content: center;
          color: #fff;
          flex-shrink: 0;
        }

        span {
          font-size: 18px;
          color: #111111;
          margin-top: 5px;
        }
      }
    }
  }

  .charged_points {
    h4 {
      font-size: 49px;
      color: $greenColor;
      margin-bottom: 6px;
      font-family: bokraFontBlack, sans-serif;
      font-weight: 900;
    }
    h5 {
      font-size: 28px;
      color: #111111;
      font-family: bokraFontMedium, sans-serif;
      margin-bottom: 0;
      font-weight: 500;
    }
  }

  .link_invitation {
    margin-bottom: 70px;

    &--tit {
      font-size: 14px;
      color: rgba(#626366, 0.5);
      margin-bottom: 5px;
    }

    &--input {
      background-color: #fff;
      border-radius: 8px;
      display: flex;
      align-items: center;
      overflow: hidden;
      border-bottom: 1px solid #cad2d7;
      border-radius: 0;
      padding-bottom: 11px;

      .v-input {
        font-size: 12px;
        color: #626366;

        &__control {
          min-height: auto;
        }

        &__slot {
          padding: 0 !important;
          box-shadow: none !important;

          .v-label {
            font-size: 12px;
          }

          input {
            padding: 0 !important;
            font-size: 16px;
            color: #111111;
          }
        }
      }

      .copy_btn {
        &.v-btn {
          height: auto !important;
          min-width: auto !important;
          padding: 0 !important;
          color: $purpleColor;

          .v-btn__content {
            .v-icon {
              color: #899097;
              font-size: 24px;
              width: 30px;
              height: 30px !important;
              display: flex;
              align-items: center;
              justify-content: center;
            }
          }
        }
      }
    }
  }

  .points_boxes {
    .points_box {
      width: 100%;
      padding: 32px;
      background-color: #fff;
      box-shadow: 0 10px 30px rgba(#202267, 0.04);

      &--tit {
        font-size: 18px;
        color: #313131;
        font-family: bokraFontMedium, sans-serif;
        margin-bottom: 19px;
        font-weight: 500;
      }

      &--desc {
        font-size: 14px;
        color: #111111;
        margin-bottom: 27px;
      }

      &--rows {
        .box-row {
          padding: 12px 16px;
          display: flex;
          align-items: center;
          justify-content: space-between;

          &:nth-child(odd) {
            background-color: #f5f6fa;
          }
          &:nth-child(even) {
            background-color: #fff;
          }

          span {
            font-size: 14px;

            &:first-child {
              color: #111111;
              font-family: bokraFontMedium, sans-serif;
              font-weight: 500;
            }
            &:last-child {
              color: #626366;
            }
          }
        }
      }
    }
  }
}
</style>
