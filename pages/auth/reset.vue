<template>
  <div class="log_pages regitser">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <h1 class="log_title reset_title">
            <span>Reset Your</span>
            <span>Password</span>
          </h1>
          <div class="title_hint reset_hint">Let’s Reset Your Password</div>
          <div class="log_form">
            <v-form>
              <div class="input_holder">
                <v-text-field
                  v-model="password"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :rules="[rules.required, rules.min]"
                  :type="show1 ? 'text' : 'password'"
                  label="New password"
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
                  label="Confirm New password"
                  hint="At least 8 characters"
                  @click:append="show1 = !show1"
                ></v-text-field>
              </div>
            </v-form>
            <v-btn class="btnStyle logButton">
              <span>Confirm</span>
              <v-icon>mdi-arrow-right</v-icon>
            </v-btn>
            <div class="or">
              <span>OR</span>
            </div>
            <nuxt-link to="" class="cancel_link">Cancel</nuxt-link>
          </div>
        </v-col>
        <v-col cols="12" md="6">
          <img src="@/assets/img/reset-bg.png" alt="" class="login_bg" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Reset",

  data() {
    return {
      show1: false,
      password: "",
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },

      confirmPassword: "",
    };
  },
};
</script>

<style lang="scss">
.log_pages {
  padding: 80px 0;

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
    font-weight: 900;

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

  &.reset_title {
    margin-bottom: 10px;
  }
}

.title_hint {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  font-size: 16px;
  color: #191a4a;
  margin-bottom: 70px;

  &.reset_hint {
    justify-content: center;
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
        font-weight: 500;
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
}

.log_pages.regitser {
  .log_title {
    width: 405px;

    @media (max-width: 575.98px) {
      width: 100%;
    }

    &.reset_title {
      width: 470px;

      @media (max-width: 575.98px) {
        width: 100%;
        font-size: 50px;
      }
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

.cancel_link {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: 500;
  font-family: bokraFontMedium, sans-serif;
  color: $greenColor !important;
  width: fit-content;
  margin: 0 auto;
  transition: 0.3s;

  &:hover {
    -webkit-text-stroke: 1px $greenColor;
    -webkit-text-fill-color: $purpleColor;
  }
}
</style>
