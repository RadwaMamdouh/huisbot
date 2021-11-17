<template>
  <div class="homepage">
    <section class="section_head">
      <img src="@/assets/img/home-section.png" alt="" class="section_head_bg" />
      <div class="section_head_content">
        <div class="container">
          <h1><span>Let’s</span> Let’s find your Next Home</h1>
          <p>
            We use cookies on our website to give you the most relevant
            experience by remembering your preferences and repeat visits. By
            clicking “Accept”, you consent to the use of ALL the cookies.
          </p>
        </div>
      </div>
      <div class="section_head_socialLinks">
        <a href="#" target="_blank">
          <img src="@/assets/img/head_twitter.svg" alt="" />
        </a>
        <a href="#" target="_blank">
          <img src="@/assets/img/head_instagram.svg" alt="" />
        </a>
        <a href="#" target="_blank">
          <img src="@/assets/img/head_facebook.svg" alt="" />
        </a>
      </div>
    </section>
    <div class="remain_home_sections">
      <section class="services">
        <div class="container">
          <v-row>
            <v-col cols="12" md="4">
              <div class="service_box">
                <div class="service_icon">
                  <img src="@/assets/img/secure.svg" alt="" />
                </div>
                <h3>Secure And Safe</h3>
                <p>
                  We offer help local nonprofits access the funding, tools,
                  training,
                </p>
              </div>
            </v-col>
            <v-col cols="12" md="4">
              <div class="service_box">
                <div class="service_icon">
                  <img src="@/assets/img/recommendations.svg" alt="" />
                </div>
                <h3>Receive Recommendations</h3>
                <p>
                  e help local nonprofits access the funding, tools, training,
                  and support.
                </p>
              </div>
            </v-col>
            <v-col cols="12" md="4">
              <div class="service_box">
                <div class="service_icon">
                  <img src="@/assets/img/points.svg" alt="" />
                </div>
                <h3>Invite Friends & Save Points</h3>
                <p>
                  Select it on eligible items when you’re shopping & choose your
                  frequency
                </p>
              </div>
            </v-col>
          </v-row>
        </div>
      </section>
      <section class="working_with_us">
        <div class="container">
          <div class="why_working_content">
            <div class="img_side">
              <h2>
                <span>Why Working</span>
                <span>With Us</span>
              </h2>
              <img src="@/assets/img/working_us.png" alt="" />
            </div>
            <div class="txt_side">
              Vanguard Properties is one of Portugal’s largest real estate
              residential developers. It has 20 urban and tourist projects in
              its portfolio spread over upmarket locations in Lisbon, Oeiras,
              Algarve and Comporta. covering a total above ground Gross Building
              Area (GBA) of around 989.259 sqm, in an investment worth more than
              €1 147 million.
            </div>
          </div>
        </div>
      </section>
      <section class="people_say">
        <Testimonials />
      </section>
    </div>
    <CompleteProfile />
  </div>
</template>

<script>
import Testimonials from "@/components/landing/Testimonials";
import CompleteProfile from "@/components/shared/CompleteProfile";

export default {
  name: "Index",
  components: {
    Testimonials,
    CompleteProfile,
  },
  layout: "landingLayout",
};
</script>

<style lang="scss" scoped>
.homepage {
  .section_head {
    background-color: $purpleColor;
    position: relative;

    @media (max-width: 575.98px) {
      height: 350px;
    }

    &_bg {
      display: block;
      width: 100%;

      #{$rtl} & {
        transform: rotateY(180deg);
      }

      @media (max-width: 575.98px) {
        height: 100%;
      }
    }

    &_content {
      position: absolute;
      top: 30%;
      left: 0;
      width: 100%;

      @media (max-width: 1256.98px) {
        top: 20%;
      }

      @media (max-width: 1060.98px) {
        padding-inline-start: 100px;
        top: 30%;
      }

      h1 {
        margin-bottom: 5px;

        @media (max-width: 800.98px) {
          margin-bottom: 15px;
        }

        &,
        span {
          font-size: 68px;
          font-family: bokraFontBold, sans-serif;
          font-weight: 700;
          width: 100%;
          max-width: 70%;
          color: #fff;
          line-height: normal;

          @media (max-width: 1256.98px) {
            font-size: 40px;
            max-width: 40%;
          }

          @media (max-width: 800.98px) {
            font-size: 25px;
            max-width: 100%;
          }
        }

        span {
          color: $greenColor;
        }
      }

      p {
        font-size: 18px;
        color: #fff;
        width: 100%;
        max-width: 65%;

        @media (max-width: 1256.98px) {
          font-size: 16px;
          max-width: 50%;
        }

        @media (max-width: 800.98px) {
          font-size: 14px;
          max-width: 95%;
        }

        @media (max-width: 575.98px) {
          font-size: 12px;
          max-width: 95%;
        }
      }
    }

    &_socialLinks {
      position: absolute;
      bottom: 79px;
      #{$ltr} & {
        left: 41px;
      }
      #{$rtl} & {
        right: 41px;
      }
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      row-gap: 17px;

      @media (max-width: 575.98px) {
        bottom: 30px;
      }

      a {
        width: 32px;
        height: 32px;
        border-radius: 100%;
        background-color: #786cda;
        box-shadow: 0 3px 6px rgba(#000000, 0.16);
        display: flex;
        align-items: center;
        justify-content: center;
        column-gap: 3px;
        font-size: 0;
        border: 2px solid transparent;
        transition: 0.3s;
        backface-visibility: hidden;

        &:hover {
          transform: scale(1.3);
          border-color: #fff;
        }
      }
    }
  }

  .remain_home_sections {
    padding: 60px 0;
    background-image: url("@/assets/img/home-huisbot.png");
    background-repeat: repeat-y;
    #{$ltr} & {
      background-position: top right -2%;

      @media (max-width: 1400.98px) {
        background-position: top right -3%;
      }
    }
    #{$rtl} & {
      background-position: top left -4%;

      @media (max-width: 1400.98px) {
        background-position: top left -3%;
      }
    }
    background-size: 170px;

    @media (max-width: 1400.98px) {
      background-size: 140px;
    }

    @media (max-width: 1024.98px) {
      background-size: 110px;
    }

    @media (max-width: 992.98px) {
      background-size: 55px;
    }

    .services {
      padding-bottom: 60px;

      .service_box {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        .service_icon {
          width: 70px;
          height: 70px;
          border-radius: 100%;
          display: flex;
          align-items: center;
          justify-content: center;
          font-size: 0;
          background-color: #fff;
          box-shadow: 0 0 45px rgba(#6353d9, 0.4);
          margin-bottom: 24px;
        }

        h3 {
          font-size: 16px;
          color: #111111;
          text-align: center;
          font-family: bokraFontMedium, sans-serif;
          font-weight: 500;
          margin-bottom: 10px;
        }

        p {
          font-size: 12px;
          color: #111111;
          margin-bottom: 0;
          text-align: center;
        }
      }
    }

    .working_with_us {
      padding: 60px 0;

      .why_working_content {
        display: flex;
        align-items: flex-start;
        justify-content: flex-end;
        column-gap: 30px;
        row-gap: 30px;

        @media (max-width: 960.98px) {
          flex-direction: column;
        }

        .img_side {
          position: relative;
          flex-basis: 70%;
          flex-shrink: 0;

          @media (max-width: 960.98px) {
            flex-basis: 100%;
          }

          img {
            width: 100%;
            height: 100%;

            #{$rtl} & {
              transform: rotateY(180deg);
            }
          }

          h2 {
            position: absolute;
            left: 50%;
            transform: translateX(-50%) translateY(-30px);
            font-size: 62px;
            color: $purpleColor;
            font-family: bokraFontBlack, sans-serif;
            font-weight: 900;
            width: 100%;
            max-width: 470px;
            text-align: end;
            z-index: 1;
            display: flex;
            flex-direction: column;

            span {
              font-family: bokraFontBlack, sans-serif;
              font-weight: 900;

              &:first-child {
                text-align: start;
              }

              &:last-child {
                text-align: end;
              }
            }

            @media (max-width: 1256.98px) {
              font-size: 50px;
              max-width: 375px;
            }

            @media (max-width: 1024.98px) {
              font-size: 46px;
              max-width: 345px;
            }

            @media (max-width: 575.98px) {
              font-size: 40px;
              max-width: 300px;
            }
          }
        }

        .txt_side {
          width: 100%;
          flex-shrink: 0;
          max-width: 44%;
          font-size: 25px;
          line-height: 50px;

          @media (max-width: 1256.98px) {
            font-size: 16px;
          }

          @media (max-width: 960.98px) {
            max-width: 100%;
          }
        }
      }
    }

    .people_say {
      padding: 60px 0;
    }
  }
}
</style>
