<template>
  <div class="testimonials">
    <div class="container">
      <h2 class="testi_title">
        <span>What People</span>
        <span>Say About Us</span>
      </h2>
      <div class="testi_slider">
        <vueper-slides
          class="no-shadow"
          ref="vueperslides1"
          :touchable="false"
          :fade="false"
          :autoplay="false"
          :bullets="false"
          @slide="
            $refs.vueperslides2.goToSlide($event.currentSlide.index, {
              emit: false,
            })
          "
          fixed-height="400px"
          :rtl="false"
        >
          <template #arrow-left>
            <img src="@/assets/img/left-arrow.svg" alt="" />
          </template>

          <template #arrow-right>
            <img src="@/assets/img/right-arrow.svg" alt="" />
          </template>
          <vueper-slide v-for="(testimonial, i) in testimonialsData" :key="i">
            <template #content>
              <div class="people_data">
                <div class="img">
                  <img
                    :src="require(`@/assets/img/${testimonial.image}`)"
                    alt=""
                  />
                </div>
                <q class="comment">
                  {{ testimonial.comment }}
                </q>
                <h4 class="name">
                  {{ testimonial.name }}
                </h4>
                <div class="role">
                  {{ testimonial.role }}
                </div>
              </div>
            </template>
          </vueper-slide>
        </vueper-slides>

        <vueper-slides
          class="no-shadow thumbnails"
          ref="vueperslides2"
          @slide="
            $refs.vueperslides1.goToSlide($event.currentSlide.index, {
              emit: false,
            })
          "
          :visible-slides="testimonialsData.length"
          fixed-height="75px"
          :bullets="false"
          :touchable="false"
          :gap="2.5"
          :arrows="false"
        >
          <vueper-slide
            v-for="(testimonial, i) in testimonialsData"
            :key="i"
            :image="require(`@/assets/img/${testimonial.image}`)"
            @click.native="$refs.vueperslides2.goToSlide(i)"
          >
          </vueper-slide>
        </vueper-slides>
      </div>
    </div>
  </div>
</template>

<script>
import { VueperSlides, VueperSlide } from "vueperslides";
import "vueperslides/dist/vueperslides.css";

export default {
  name: "Testimonials",
  components: { VueperSlides, VueperSlide },
  data() {
    return {
      slides: [
        { image: require("@/assets/img/people1.png") },
        { image: require("@/assets/img/people2.png") },
        { image: require("@/assets/img/people3.png") },
      ],
      testimonialsData: [
        {
          image: "people1.png",
          comment:
            "Forge links to your account on one of our supported cloud providers. Or, you can even provision a VPS on the custom provider of your choice.Forge links to your account on one of ",
          name: "Ahmed Salah",
          role: "CEO of Wady",
        },
        {
          image: "people2.png",
          comment:
            "Forge links to your account on one of our supported cloud providers. Or, you can even provision a VPS on the custom provider of your choice.Forge links to your account on one of ",
          name: "Mustafa Salah",
          role: "CEO of Wady",
        },
        {
          image: "people3.png",
          comment:
            "Forge links to your account on one of our supported cloud providers. Or, you can even provision a VPS on the custom provider of your choice.Forge links to your account on one of ",
          name: "Khaled Salah",
          role: "CEO of Wady",
        },
        {
          image: "people4.png",
          comment:
            "Forge links to your account on one of our supported cloud providers. Or, you can even provision a VPS on the custom provider of your choice.Forge links to your account on one of ",
          name: "Omar Salah",
          role: "CEO of Wady",
        },
        {
          image: "people5.png",
          comment:
            "Forge links to your account on one of our supported cloud providers. Or, you can even provision a VPS on the custom provider of your choice.Forge links to your account on one of ",
          name: "Muhammed Salah",
          role: "CEO of Wady",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.testimonials {
  background-image: url("@/assets/img/testi-section-bg.png");
  background-repeat: no-repeat;
  background-size: 100% 95%;
  background-position: center;
  min-height: 700px;

  @media (max-width: 600.98px) {
    min-height: 570px;
  }

  .testi_title {
    font-size: 62px;
    font-family: bokraFontBlack, sans-serif;
    font-weight: 900;
    margin-bottom: 5px;
    color: $purpleColor;
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 56%;
    line-height: normal;
    transform: translateY(-30px);

    @media (max-width: 992.98px) {
      font-size: 40px;
    }

    @media (max-width: 575.98px) {
      font-size: 20px;
      transform: translateY(-10px);
    }

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
  }
}

.testi_slider {
  background-image: url(/_nuxt/assets/img/testimonials-bg.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  width: 100%;
  max-width: 60%;
  margin: 0 auto;
  height: 400px;

  @media (max-width: 992.98px) {
    max-width: 100%;
  }

  @media (max-width: 600.98px) {
    height: 350px;
  }

  .people_data {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding: 0 60px;

    @media (max-width: 600.98px) {
      padding: 0 10px;
    }

    .img {
      width: 131px;
      height: 131px;
      margin: 0 auto 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 100%;
      border: 13px solid $purpleColor;

      @media (max-width: 600.98px) {
        width: 100px;
        height: 100px;
      }

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    .comment {
      font-size: 16px;
      color: #111111;
      margin-bottom: 10px;
      position: relative;
      width: 100%;
      max-width: calc(100% - 48px);
      word-break: break-word;

      @media (max-width: 600.98px) {
        font-size: 14px;
      }

      &::before,
      &::after {
        color: $purpleColor;
      }

      &::before {
        content: url("@/assets/img/double-quote-left.svg");
        position: absolute;
        #{$ltr} & {
          left: -24px;
        }
        #{$rtl} & {
          right: -24px;
          transform: rotateY(180deg);
        }
        top: -18px;
      }

      &::after {
        content: url("@/assets/img/double-quote-right.svg");
        position: absolute;
        #{$ltr} & {
          right: -22px;
        }
        #{$rtl} & {
          left: -22px;
          transform: rotateY(180deg);
        }
        bottom: -18px;
      }
    }

    .name {
      font-size: 18px;
      font-family: bokraFontMedium, sans-serif;
      font-weight: 500;
      color: $purpleColor;
      margin-bottom: 12px;
      text-align: center;

      @media (max-width: 600.98px) {
        font-size: 16px;
      }
    }

    .role {
      font-size: 14px;
      color: #111111;
      text-align: center;

      @media (max-width: 600.98px) {
        font-size: 12px;
      }
    }
  }

  .vueperslides {
    @media (max-width: 600.98px) {
      height: 100% !important;
      margin-bottom: 20px;
    }

    &__arrows {
      .vueperslides__arrow {
        width: 54px;
        height: 54px;
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #000;
        color: #fff;
        opacity: 1;

        &--prev {
          bottom: 0;
          transform: none;
          top: auto;
          #{$ltr} & {
            left: 10%;
          }
          #{$rtl} & {
            right: 10%;
          }

          img {
            transform: rotate(90deg);
          }
        }

        &--next {
          bottom: 0;
          transform: none;
          top: auto;
          #{$ltr} & {
            right: 10%;
          }
          #{$rtl} & {
            left: 10%;
          }

          img {
            transform: rotate(90deg);
          }
        }

        &:hover {
          box-shadow: 0 0 9px 4px rgba($purpleColor, 0.3);
        }
      }
    }
  }
}

// .thumbnails {
//   margin: auto;
//   max-width: 300px;
// }

.thumbnails {
  .vueperslides__parallax-wrapper {
    overflow: visible !important;
  }

  .vueperslides__track {
    overflow: visible !important;

    &-inner {
      @media (max-width: 992.98px) {
        justify-content: center;
      }
    }
  }
}

.thumbnails .vueperslide {
  box-sizing: border-box;
  border: 9px solid $greenColor;
  transition: 0.3s ease-in-out;
  cursor: pointer;
  width: 83px !important;
  height: 83px !important;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0.69;
  position: absolute;
  z-index: 1;

  @media (max-width: 600.98px) {
    width: 60px !important;
    height: 60px !important;
  }

  @media (max-width: 992.98px) {
    position: relative;
  }

  &:nth-child(1) {
    top: -350px;
    #{$ltr} & {
      left: -30%;
    }
    #{$rtl} & {
      right: -30%;
    }

    @media (max-width: 992.98px) {
      top: 0;
      #{$ltr} & {
        left: 0;
      }
      #{$rtl} & {
        right: 0;
      }
    }
  }

  &:nth-child(2) {
    top: -215px;
    #{$ltr} & {
      left: -18%;
    }
    #{$rtl} & {
      right: -18%;
    }

    @media (max-width: 992.98px) {
      top: 0;
      #{$ltr} & {
        left: 0;
      }
      #{$rtl} & {
        right: 0;
      }
    }
  }

  &:nth-child(3) {
    top: 0;
    left: 50%;
    transform: translateX(-50%);

    @media (max-width: 992.98px) {
      top: 0;
      left: 0;
      transform: none;
    }
  }

  &:nth-child(4) {
    top: -215px;
    #{$ltr} & {
      right: -18%;
    }
    #{$rtl} & {
      left: -18%;
    }

    @media (max-width: 992.98px) {
      top: 0;
      #{$ltr} & {
        left: 0;
      }
      #{$rtl} & {
        right: 0;
      }
    }
  }

  &:nth-child(5) {
    top: -350px;
    #{$ltr} & {
      right: -30%;
    }
    #{$rtl} & {
      left: -30%;
    }

    @media (max-width: 992.98px) {
      top: 0;
      #{$ltr} & {
        left: 0;
      }
      #{$rtl} & {
        right: 0;
      }
    }
  }
}

.thumbnails .vueperslide--active {
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.3);
  opacity: 1;
  border-color: $purpleColor;
}
</style>
