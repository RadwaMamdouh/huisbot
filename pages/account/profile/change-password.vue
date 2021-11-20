<template>
  <div class="edit_page">
    <div class="edit_head">
      <div class="left">
        <nuxt-link to="" @click.native.prevent="$router.go(-1)">
          <img src="@/assets/img/back-arrow.svg" alt="" class="back_btn" />
        </nuxt-link>
        <h2>Change password</h2>
      </div>
      <div class="right">
        <nuxt-link to="/account/profile" class="not_now" text>Cancel</nuxt-link>
        <v-btn class="complete" text>Save</v-btn>
      </div>
    </div>
    <v-form>
      <v-row>
        <v-col cols="12" md="12">
          <div class="input_holder">
            <v-text-field
              v-model="currentPassword"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              label="Current Password"
              placeholder="Please Enter Your Current Password"
              hint="At least 8 characters"
              @click:append="show1 = !show1"
            ></v-text-field>
          </div>
        </v-col>
        <v-col cols="12" md="12">
          <div class="input_holder">
            <v-text-field
              v-model="newPassword"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              label="New Password"
              placeholder="Please Enter Your New Password"
              hint="At least 8 characters"
              @click:append="show1 = !show1"
            ></v-text-field>
          </div>
        </v-col>
        <v-col cols="12" md="12">
          <div class="input_holder">
            <v-text-field
              v-model="confirmPassword"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              label="Re-Type New Password"
              placeholder="Please Retype Your New Password To Confirm It"
              hint="At least 8 characters"
              @click:append="show1 = !show1"
            ></v-text-field>
          </div>
        </v-col>
      </v-row>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "change-password",
  layout: "loggedLayout",

  data() {
    return {
      show1: false,
      currentPassword: "",
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },

      newPassword: "",
      confirmPassword: "",
    };
  },
};
</script>

<style lang="scss">
.edit_page {
  .edit_head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 30px;

    @media (max-width: 600.98px) {
      flex-wrap: wrap;
      row-gap: 20px;
    }

    .left {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      column-gap: 16px;

      a {
        flex-shrink: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 0;
        width: 32px;
        height: 32px;
        border-radius: 100%;
        background-color: #e6e8ff;
        border: 1px solid transparent;
        transition: 0.3s;

        img {
          #{$rtl} & {
            transform: rotate(180deg);
          }
        }

        &:hover {
          border-color: $purpleColor;
        }
      }

      h2 {
        font-size: 25px;
        color: #111111;
        font-family: bokraFontMedium, sans-serif;
        margin-bottom: 0;
        font-weight: 500;

        @media (max-width: 1024.98px) {
          font-size: 20px;
        }
      }
    }

    .right {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      column-gap: 16px;

      @media (max-width: 600.98px) {
        width: 100%;
        justify-content: flex-end;
      }

      .v-btn {
        @extend %btn;
        padding: 8px 18px !important;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 5px;

        &.complete {
          @include buttonStyle($purpleColor, #fff, $purpleColor);

          .v-btn__content {
            font-size: 14px;
            text-transform: capitalize;
          }
        }
      }

      .not_now {
        padding: 8px 18px !important;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 5px;
        border: 1px solid #f1f1f1;
        text-decoration: none;
        font-size: 14px;
        text-transform: capitalize;
        color: $purpleColor;
        line-height: normal;
        transition: 0.3s;

        &:hover {
          background-color: $purpleColor;
          color: #fff;
        }
      }
    }
  }

  .input_holder {
    .v-input {
      &__icon {
        .v-icon {
          &.mdi-eye {
            color: $purpleColor;
          }
        }
      }
    }
  }
}
</style>
