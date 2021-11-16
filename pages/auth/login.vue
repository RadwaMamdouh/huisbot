<template>
  <div class="log_pages">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <img src="@/assets/img/login-bg.png" alt="" class="login_bg" />
        </v-col>
        <v-col cols="12" md="6">
          <h1 class="log_title">
            <span>Welcome</span>
            <span>Back</span>
          </h1>
          <div class="log_form">
            <v-form>
              <div class="input_holder">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="Email Address"
                  required
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
            </v-form>
            <nuxt-link to="forget" class="forget_password">
              Forget Password?
            </nuxt-link>
            <v-btn class="btnStyle logButton">
              <span>LOGIN</span>
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
              <span>Don’t have account?</span>
              <nuxt-link to="register">Sign Up</nuxt-link>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Login',

  data() {
    return {
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
      show1: false,
      password: '',
      rules: {
        required: (value) => !!value || 'Required.',
        min: (v) => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => `The email and password you entered don't match`,
      },
    }
  },
}
</script>

<style lang="scss">
.log_pages {
  padding: 80px 0;
  position: relative;

  .login_bg {
    position: absolute;
    top: 80px;
    #{$ltr} & {
      left: 0;
    }
    #{$rtl} & {
      right: 0;
      transform: rotateY(180deg);
    }
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

  @media (max-width: 575.98px) {
    font-size: 50px;
  }

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
  padding-inline-start: 75px;

  @media (max-width: 1024.98px) {
    padding-inline-start: 60px;
  }

  @media (max-width: 992.98px) {
    padding-inline-start: 0;
  }

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

  .forget_password {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    margin-bottom: 58px;
    font-size: 14px;
    font-weight: 500;
    font-family: bokraFontMedium, sans-serif;
    color: $greenColor;
    width: fit-content;
    margin-inline-start: auto;
    transition: 0.3s;

    &:hover {
      -webkit-text-stroke: 1px $greenColor;
      -webkit-text-fill-color: $purpleColor;
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
        content: '';
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
</style>
