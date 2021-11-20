<template>
  <div class="log_pages regitser">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <h1 class="log_title">
            <span>Create</span>
            <span>Account</span>
          </h1>
          <div class="log_form">
            <v-form>
              <div class="input_holder">
                <v-text-field
                  v-model="name"
                  :rules="nameRules"
                  label="Name"
                  required
                ></v-text-field>
              </div>
              <div class="input_holder">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="Email"
                  required
                ></v-text-field>
              </div>
              <div class="input_holder country_phone">
                <v-select
                  v-model="select"
                  :items="items"
                  item-value="code"
                  label="Code Number"
                  solo
                  :menu-props="{
                    bottom: true,
                    offsetY: true,
                    contentClass: 'codeNumber_menu',
                  }"
                  hide-details="true"
                  class="code_number"
                >
                  <template #selection="{ item }">
                    <span>{{ item.name }}</span>
                    <img :src="require(`@/assets/img/${item.image}`)" />
                  </template>
                  <template #item="{ item }">
                    <span>{{ item.name }}</span>
                    <img :src="require(`@/assets/img/${item.image}`)" />
                  </template>
                </v-select>
                <v-text-field
                  v-model="phoneNumber"
                  label="Phone"
                  required
                  class="phone_number"
                ></v-text-field>
              </div>
              <div class="input_holder">
                <v-text-field
                  v-model="password"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :rules="[rules.required, rules.min]"
                  :type="show1 ? 'text' : 'password'"
                  label="Password"
                  hint="At least 8 characters"
                  @click:append="show1 = !show1"
                ></v-text-field>
              </div>
              <div class="input_holder">
                <v-text-field
                  v-model="confirmPassword"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :rules="[rules.required, rules.min]"
                  :type="show1 ? 'text' : 'password'"
                  label="Confirm password"
                  hint="At least 8 characters"
                  @click:append="show1 = !show1"
                ></v-text-field>
              </div>
            </v-form>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>
                  By clicking you will be agreeing to terms and conditions.
                </span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>
                  By clicking you will be agreeing to terms and conditions.
                </span>
              </label>
            </div>
            <v-btn class="btnStyle logButton">
              <span>Sign Up</span>
              <v-icon>mdi-arrow-right</v-icon>
            </v-btn>
            <div class="or">
              <span>OR</span>
            </div>
            <div class="socila_links">
              <a href="#" target="_blank">
                <img src="@/assets/img/facebook-icon.svg" alt="" />
              </a>
              <a href="#" target="_blank">
                <img src="@/assets/img/google-icon.svg" alt="" />
              </a>
              <a href="#" target="_blank">
                <img src="@/assets/img/instagram-icon.svg" alt="" />
              </a>
            </div>
            <div class="have_account">
              <span>already have an account?</span>
              <nuxt-link to="login">Log in</nuxt-link>
            </div>
          </div>
        </v-col>
        <v-col cols="12" md="6">
          <img src="@/assets/img/register-bg.png" alt="" class="login_bg" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Register",
  data() {
    return {
      name: "",
      nameRules: [
        (v) => !!v || "Name is required",
        (v) => v.length <= 10 || "Name must be less than 10 characters",
      ],

      email: "",
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+/.test(v) || "E-mail must be valid",
      ],

      show1: false,
      password: "",
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },

      confirmPassword: "",
      phoneNumber: "",

      select: { name: "+31", image: "flag.svg", code: "00" },
      items: [
        {
          name: "+31",
          image: "flag.svg",
          code: "00",
        },
        {
          name: "+21",
          image: "flag.svg",
          code: "01",
        },
        {
          name: "+11",
          image: "flag.svg",
          code: "02",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.log_pages {
  padding: 80px 0;
  position: relative;

  .login_bg {
    position: absolute;
    top: 80px;
    width: 100%;
    max-width: 50%;
    height: auto;
    max-height: calc(100% - 160px);

    @media (max-width: 952.98px) {
      height: auto;
      position: relative;
      width: 100%;
      max-width: none;
      max-height: none;
      top: 0;
    }
  }
}

.log_title {
  font-size: 62px;
  font-weight: 900;
  font-family: bokraFontBlack, sans-serif;
  color: $purpleColor;
  display: flex;
  flex-direction: column;
  width: fit-content;
  line-height: normal;
  margin-bottom: 30px;

  span {
    font-family: bokraFontBlack, sans-serif;

    &:first-child {
      #{$ltr} & {
        text-align: left;
      }
      #{$rtl} & {
        text-align: right;
      }
    }
    &:last-child {
      #{$ltr} & {
        text-align: right;
      }
      #{$rtl} & {
        text-align: left;
      }
    }
  }
}

.log_form {
  .v-form {
    margin-bottom: 10px;
  }

  .input_holder {
    &:not(:last-child) {
      margin-bottom: 10px;
    }

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

  .logButton {
    @include buttonStyle($purpleColor, #fff, $purpleColor);
    padding: 12px 24px !important;
    width: 100%;
    position: relative;
    margin-bottom: 45px;

    .v-btn__content {
      span {
        font-family: bokraFontMedium, sans-serif;
      }
    }

    .v-icon {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      #{$ltr} & {
        right: 24px;
      }
      #{$rtl} & {
        left: 24px;
        transform: translateY(-50%) rotate(180deg);
      }
      font-size: 18px;
      transition: 0.3s;
    }

    &:hover {
      .v-icon {
        #{$ltr} & {
          animation: arrow 1.3s infinite;
        }
        #{$rtl} & {
          animation: arrowAR 1.3s infinite;
        }
      }
    }
  }

  .or {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 28px;
    position: relative;

    span {
      font-size: 16px;
      color: #111111;

      &::before,
      &::after {
        content: "";
        height: 1px;
        width: 100%;
        background-color: #d8d2f6;
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        width: 100%;
        max-width: 45%;
      }

      &::before {
        left: 0;
      }

      &::after {
        right: 0;
      }
    }
  }

  .socila_links {
    margin-bottom: 25px;
    display: flex;
    align-items: center;
    justify-content: center;
    column-gap: 24px;

    a {
      width: 48px;
      height: 48px;
      border-radius: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: #fff;
      box-shadow: 0 0 42px rgba($purpleColor, 0.29);
      transition: 0.3s;
      backface-visibility: hidden;

      &:hover {
        transform: scale(0.8);
      }
    }
  }

  .have_account {
    display: flex;
    align-items: center;
    justify-content: center;
    column-gap: 14px;

    span {
      font-size: 14px;
      color: #626366;
    }

    a {
      font-size: 14px;
      font-weight: 500;
      font-family: bokraFontMedium, sans-serif;
      color: $greenColor;
      transition: 0.3s;

      &:hover {
        -webkit-text-stroke: 1px $greenColor;
        -webkit-text-fill-color: $purpleColor;
      }
    }
  }
}

.log_pages.regitser {
  .log_title {
    width: 405px;

    @media (max-width: 575.98px) {
      width: 100%;
      font-size: 50px;
    }
  }

  .login_bg {
    #{$ltr} & {
      right: 0;
      left: auto;
    }
    #{$rtl} & {
      right: auto;
      left: 0;
      transform: rotateY(-180deg);
    }
  }

  .log_form {
    padding-inline-start: 0;
  }
}

@keyframes arrow {
  0% {
    transform: translateY(-50%) translateX(0);
  }
  50% {
    transform: translateY(-50%) translateX(10px);
  }
  100% {
    transform: translateY(-50%) translateX(0);
  }
}

@keyframes arrowAR {
  0% {
    transform: translateY(-50%) rotate(180deg) translateX(0);
  }
  50% {
    transform: translateY(-50%) rotate(180deg) translateX(10px);
  }
  100% {
    transform: translateY(-50%) rotate(180deg) translateX(0);
  }
}

.code_number {
  max-width: 16%;
  position: relative;

  &::after {
    content: "";
    width: 1px;
    height: 20px;
    background-color: #dee2e6;
    position: absolute;
    #{$ltr} & {
      right: -5px;

      @media (max-width: 575.98px) {
        right: -12px;
      }
    }
    #{$rtl} & {
      left: -5px;

      @media (max-width: 575.98px) {
        left: -12px;
      }
    }
    top: 7px;
  }

  &.v-input {
    .v-input__control {
      min-height: auto !important;
      border-bottom: 1px solid rgba(0, 0, 0, 0.42);
      border-radius: 0;
      margin-bottom: 5px;
    }
    .v-input__slot {
      box-shadow: none !important;
      padding: 0 !important;

      .v-select__selections {
        font-size: 14px;
        font-weight: 500;
        font-family: bokraFontMedium, sans-serif;

        & > span {
          margin-inline-end: 18px;
        }

        .v-select__selection {
          max-width: 100% !important;
          margin: 0 !important;
          overflow: unset !important;
        }

        input {
          width: 0;
        }
      }
    }
  }
}

.country_phone {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.codeNumber_menu {
  .v-list {
    &-item {
      column-gap: 5px;
    }
  }
}

.phone_number {
  .v-input {
    &__slot {
      .v-label {
        #{$ltr} & {
          left: 20px !important;
        }
        #{$rtl} & {
          right: 20px !important;
        }
      }

      input {
        padding-inline-start: 20px;
      }
    }
  }
}

.checkboxes {
  margin-bottom: 38px;

  .custom_checkbox {
    &:not(:last-child) {
      margin-bottom: 20px;
    }
  }
}

.custom_checkbox {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  column-gap: 13px;
  cursor: pointer;

  .v-icon {
    width: 28px;
    height: 28px;
    padding: 2px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 2px rgba($purpleColor, 0.4);
    color: transparent;
    transition: 0.3s;
  }

  input:checked ~ .v-icon {
    color: $greenColor;
  }
}
</style>
