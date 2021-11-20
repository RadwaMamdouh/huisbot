<template>
  <div class="edit_page">
    <div class="edit_head">
      <div class="left">
        <nuxt-link to="" @click.native.prevent="$router.go(-1)">
          <img src="@/assets/img/back-arrow.svg" alt="" class="back_btn" />
        </nuxt-link>
        <h2>Edit Address Information</h2>
      </div>
      <div class="right">
        <nuxt-link to="/account/" class="not_now" text>Cancel</nuxt-link>
        <v-btn class="complete" text>Save</v-btn>
      </div>
    </div>
    <v-form>
      <v-row>
        <v-col cols="12" md="6">
          <div class="input_holder">
            <v-select
              :items="items"
              label="Region"
              placeholder="Select Option"
              required
            ></v-select>
          </div>
        </v-col>
        <v-col cols="12" md="6">
          <div class="input_holder">
            <v-text-field
              label="Zip Code"
              placeholder="Enter Zip Code"
              required
            ></v-text-field>
          </div>
        </v-col>
        <v-col cols="12" md="12">
          <div class="input_holder">
            <v-text-field
              label="Address"
              placeholder="Please Enter Your Address"
              required
            ></v-text-field>
          </div>
        </v-col>
      </v-row>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "edit-address",
  layout: "loggedLayout",

  data() {
    return {
      items: ["Dasman", "Al Salmia"],
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
      }
    }

    .right {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      column-gap: 16px;

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

  .v-select {
    .v-input__icon {
      .v-icon {
        color: #3337a5;
      }
    }
  }
}
</style>
