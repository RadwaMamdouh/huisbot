<template>
  <div class="toast_holder" :hidden="hide">
    <img src="@/assets/img/toast-bg.png" alt="" />
    <div class="toast_content">
      <div class="head">
        <div class="icon" v-if="icon">
          <v-icon>mdi-check</v-icon>
        </div>
        <div class="tit">{{ msgTitle }}</div>
      </div>
      <div class="txt">{{ msgContent }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToastMsg",

  props: {
    icon: {
      type: Boolean,
      required: true,
    },
    msgTitle: {
      type: String,
    },
    msgContent: {
      type: String,
    },
  },

  data() {
    return {
      hide: false,
    };
  },

  mounted() {
    setTimeout(() => {
      this.hide = true;
    }, 3000);
  },
};
</script>

<style lang="scss" scoped>
.toast_holder {
  position: absolute;
  top: 65px;
  #{$ltr} & {
    right: 0;
  }
  #{$rtl} & {
    left: 0;
  }

  height: 120px;

  @media (max-width: 600.98px) {
    height: 110px;
  }

  & > img {
    width: 100%;
    height: 100%;

    #{$rtl} & {
      transform: rotateY(180deg);
    }
  }

  .toast_content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    #{$ltr} & {
      padding: 12px 16px 12px 59px;
    }
    #{$rtl} & {
      padding: 12px 59px 12px 16px;
    }

    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;

    .head {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      column-gap: 7px;
      margin-bottom: 5px;

      .icon {
        width: 36px;
        height: 36px;
        background-color: rgba($purpleColor, 0.47);
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 5px;

        .v-icon {
          width: 26px;
          height: 26px;
          border-radius: 100%;
          display: flex;
          align-items: center;
          justify-content: center;
          background-color: $purpleColor;
          color: #fff;
          font-size: 20px;
        }
      }

      .tit {
        font-size: 18px;
        color: $purpleColor;
        font-family: bokraFontMedium, sans-serif;
        font-weight: 500;

        @media (max-width: 600.98px) {
          font-size: 14px;
        }
      }
    }

    .txt {
      font-size: 18px;
      color: #fff;

      @media (max-width: 600.98px) {
        font-size: 14px;
      }
    }
  }
}
</style>
