<template>
  <div class="log_pages">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <img src="@/assets/img/forget-bg.png" alt="" class="login_bg" />
        </v-col>
        <v-col cols="12" md="6">
          <h1 class="log_title forget_title">
            <span>Forget</span>
            <span>Password</span>
          </h1>
          <div class="title_hint">
            Enter Your Email Address To Reset The Password
          </div>
          <div class="log_form">
            <v-form>
              <div class="input_holder">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="Email"
                  required
                ></v-text-field>
              </div>
            </v-form>
            <v-btn class="btnStyle logButton">
              <span>Reset</span>
              <v-icon>mdi-arrow-right</v-icon>
            </v-btn>
            <div class="or">
              <span>OR</span>
            </div>
            <nuxt-link to="" class="cancel_link">Cancel</nuxt-link>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Forget',

  data() {
    return {
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
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

  &.forget_title {
    width: 400px;
    margin-bottom: 10px;

    @media (max-width: 575.98px) {
      width: 100%;
    }
  }
}

.title_hint {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  font-size: 16px;
  color: #191a4a;
  margin-bottom: 70px;
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
