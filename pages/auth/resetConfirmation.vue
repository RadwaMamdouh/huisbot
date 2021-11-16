<template>
  <div class="reset_confirmation">
    <v-container>
      <img src="@/assets/img/reset-confirmation.png" alt="" class="reset_img" />
      <h1>Rest Password</h1>
      <p>We have sent a password recovery Instructions to your mail</p>
      <p class="dont_receive">
        Don’t receive the email? Please check your Spam files or
        <nuxt-link to="">Try another email address</nuxt-link>
      </p>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'ResetConfirmation',
}
</script>

<style lang="scss">
.reset_confirmation {
  padding: 80px 0;

  .reset_img {
    display: block;
    max-width: 60%;
    margin: 0 auto 20px;

    @media (max-width: 1024.98px) {
      max-width: 80%;
    }

    @media (max-width: 992.98px) {
      max-width: 90%;
    }

    @media (max-width: 575.98px) {
      max-width: 100%;
    }
  }

  h1 {
    font-size: 62px;
    font-weight: 900;
    font-family: bokraFontBlack, sans-serif;
    color: $purpleColor;
    text-align: center;
    margin-bottom: 20px;

    @media (max-width: 575.98px) {
      font-size: 35px;
    }
  }

  p {
    font-size: 16px;
    color: #191a4a;
    text-align: center;
    max-width: 30%;
    margin: 0 auto 16px;

    @media (max-width: 1024.98px) {
      max-width: 35%;
    }

    @media (max-width: 992.98px) {
      max-width: 50%;
    }

    @media (max-width: 575.98px) {
      max-width: 75%;
    }

    &.dont_receive {
      font-size: 14px;
      color: #6b6c7d;
      max-width: 34%;
      margin-bottom: 0;

      @media (max-width: 1024.98px) {
        max-width: 45%;
      }

      @media (max-width: 992.98px) {
        max-width: 54%;
      }

      @media (max-width: 575.98px) {
        max-width: 100%;
      }

      a {
        color: $greenColor;
        font-weight: 500;
        font-family: bokraFontMedium, sans-serif;
        transition: 0.3s;

        &:hover {
          -webkit-text-stroke: 1px $greenColor;
          -webkit-text-fill-color: $purpleColor;
        }
      }
    }
  }
}
</style>
