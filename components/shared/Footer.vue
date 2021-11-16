<template>
  <v-footer>
    <div class="app_footer">
      <v-container>
        <div class="top">
          <v-row>
            <v-col cols="12" md="4">
              <div class="logo">
                <img src="@/assets/img/Huisbot-white.png" alt="" />
              </div>
              <div class="description">
                Defining interaction patterns best suited in the
                contextefining.Defining interaction patterns best suited in the
                contextefining
              </div>
              <div class="payment_socialLinks">
                <div class="payment">
                  <div class="tit">Payments</div>
                  <div class="payment_icons">
                    <img src="@/assets/img/mastercard.svg" alt="" />
                    <img src="@/assets/img/visa.svg" alt="" />
                  </div>
                </div>
                <div class="social_links">
                  <a href="#" target="_blank">
                    <img src="@/assets/img/facebook.svg" alt="" />
                  </a>
                  <a href="#" target="_blank">
                    <img src="@/assets/img/twitter.svg" alt="" />
                  </a>
                  <a href="#" target="_blank">
                    <img src="@/assets/img/instagram.svg" alt="" />
                  </a>
                </div>
              </div>
            </v-col>
            <v-col cols="12" md="2">
              <div class="links_tit">Information</div>
              <div class="links">
                <nuxt-link to="/about">About Us</nuxt-link>
                <nuxt-link to="/privacy">Privacy Policy</nuxt-link>
                <nuxt-link to="/terms">Terms & Conditions</nuxt-link>
              </div>
            </v-col>
            <v-col cols="12" md="2">
              <div class="links_tit">Extras</div>
              <div class="links">
                <nuxt-link to="/help">Help</nuxt-link>
                <nuxt-link to="/faq">FAQ</nuxt-link>
                <nuxt-link to="/contact">Contact us</nuxt-link>
              </div>
            </v-col>
            <v-col cols="12" md="4">
              <div class="links_tit">Join our List</div>
              <div class="description">
                Sign up now and be the first to know about exclusive offers,
                product updates, and exciting news and announcements.
              </div>
              <div class="subscripe">
                <input
                  type="email"
                  name="email"
                  placeholder="Enter your email"
                />
                <v-btn>Subscribe</v-btn>
              </div>
            </v-col>
          </v-row>
        </div>
        <div class="copyRights">Copyright © Logo 2020. All Rights Reserved</div>
      </v-container>
    </div>
  </v-footer>
</template>

<script>
export default {
  name: 'Footer',
}
</script>

<style lang="scss">
.v-footer {
  background-color: $purpleColor !important;
  background-image: url('@/assets/img/footer-bg.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: bottom;
  padding: 22px 0;
}

.app_footer {
  width: 100%;
  height: 100%;

  .top {
    margin-bottom: 60px;

    .logo {
      margin-bottom: 25px;
      height: 41px;
    }

    .description {
      color: #fff;
      font-size: 12px;
      margin-bottom: 14px;
      line-height: 24px;
    }

    .payment_socialLinks {
      display: flex;
      align-items: center;
      justify-content: space-between;

      .payment {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        row-gap: 10px;

        .tit {
          color: $greenColor;
          font-size: 14px;
          font-weight: 500;
          font-family: bokraFontMedium, sans-serif;
        }

        .payment_icons {
          display: flex;
          align-items: center;
          justify-content: flex-start;
          column-gap: 15px;
        }
      }

      .social_links {
        display: flex;
        align-items: center;
        justify-content: flex-end;
        column-gap: 8px;

        a {
          font-size: 0;
          transition: 0.3s;

          &:hover {
            transform: translateY(-3px);
          }
        }
      }
    }

    .links_tit {
      color: $greenColor;
      font-size: 16px;
      font-weight: 500;
      margin-bottom: 25px;
      font-family: bokraFontMedium, sans-serif;
    }

    .links {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: flex-start;
      row-gap: 22px;

      a {
        color: #fff;
        font-size: 14px;
        text-decoration: none;
        position: relative;

        &::before {
          content: '';
          position: absolute;
          bottom: 0;
          #{$ltr} & {
            left: 0;
          }
          #{$rtl} & {
            right: 0;
          }
          height: 1px;
          background-color: #fff;
          width: 0;
          opacity: 0;
          visibility: hidden;
          transition: 0.3s;
        }

        &:hover {
          &::before {
            width: 100%;
            opacity: 1;
            visibility: visible;
          }
        }
      }
    }

    .subscripe {
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: #fff;
      border-radius: 5px;
      height: 40px;
      overflow: hidden;

      input {
        width: 100%;
        padding: 12px 24px;
        font-size: 14px;
        outline: 0 none;

        &::placeholder {
          font-size: 12px;
          color: #cad2d7;
        }
      }

      .v-btn {
        flex-shrink: 0;
        min-width: unset !important;
        height: 100%;
        padding: 12px 24px;
        background-color: $greenColor;
        color: $purpleColor;
        font-size: 14px;
        #{$ltr} & {
          border-top-left-radius: 5px;
          border-bottom-left-radius: 5px;
        }
        #{$rtl} & {
          border-top-right-radius: 5px;
          border-bottom-right-radius: 5px;
        }
      }
    }
  }

  .copyRights {
    font-size: 12px;
    color: #fff;
    text-align: center;
  }
}
</style>
