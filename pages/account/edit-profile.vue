<template>
  <div class="edit_page">
    <div class="edit_head">
      <div class="left">
        <nuxt-link to="" @click.native.prevent="$router.go(-1)">
          <img src="@/assets/img/back-arrow.svg" alt="" class="back_btn" />
        </nuxt-link>
        <h2>Edit Personal Information</h2>
      </div>
      <div class="right">
        <nuxt-link to="/account/" class="not_now" text>Cancel</nuxt-link>
        <v-btn class="complete" text>Save</v-btn>
      </div>
    </div>
    <div class="edit_profile_form">
      <v-form>
        <v-row>
          <v-col cols="12" md="12">
            <label class="profile_pic_holder">
              <input type="file" class="d-none" />
              <div class="profile_pic">
                <img src="@/assets/img/profile-pic.png" alt="" />
              </div>
              <div class="cam_icon">
                <img src="@/assets/img/camera-icon.svg" alt="" />
              </div>
            </label>
          </v-col>
          <v-col cols="6" md="6">
            <div class="input_holder">
              <v-text-field
                v-model="name"
                :rules="nameRules"
                label="Name"
                required
              ></v-text-field>
            </div>
          </v-col>
          <v-col cols="6" md="6">
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
          </v-col>
          <v-col cols="12" md="12">
            <div class="input_holder">
              <v-text-field
                v-model="email"
                :rules="emailRules"
                label="Email Address"
                required
              ></v-text-field>
            </div>
          </v-col>
          <v-col cols="12" md="12">
            <div class="input_holder">
              <v-textarea
                name="input-7-1"
                label="Description"
                value="In Publishing And Graphic Design, Lorem Ipsum Is A Placeholder Text Commonly Used To Demonstrate The Visual Form Of A Document Or A Typeface Without Relying On Meaningful Content. Lorem Ipsum May Be Used As A Placeholder Before Final Copy Is Available."
                no-resize="true"
              ></v-textarea>
            </div>
          </v-col>
        </v-row>
      </v-form>
    </div>
    <nuxt-link to="change-password" class="change_password">
      Change password
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: "edit-profile",
  layout: "loggedLayout",

  data() {
    return {
      name: "",
      nameRules: [
        (v) => !!v || "Name is required",
        (v) => v.length <= 10 || "Name must be less than 10 characters",
      ],

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

      email: "",
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+/.test(v) || "E-mail must be valid",
      ],
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

  .edit_profile_form {
    margin-bottom: 40px;

    .profile_pic_holder {
      position: relative;
      width: 157px;
      height: 157px;
      border-radius: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto;
      cursor: pointer;
      transition: 0.3s;

      .profile_pic {
        width: 157px;
        height: 157px;
        border: 7px solid #fff;
        box-shadow: 0 0 42px rgba(#3337a5, 0.13);
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0 auto;
        overflow: hidden;

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          border-radius: 100%;
        }
      }

      .cam_icon {
        position: absolute;
        width: 40px;
        height: 40px;
        border-radius: 100%;
        background-color: #e6e8ff;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 0;
        #{$ltr} & {
          right: 0;
        }
        #{$rtl} & {
          left: 0;
        }
        bottom: 0;
        border: 1px solid transparent;
        transition: 0.3s;
      }

      &:hover {
        opacity: 0.7;

        .cam_icon {
          border-color: $purpleColor;
          top: 50%;
          #{$ltr} & {
            left: 50%;
            transform: translate(-50%, -50%);
          }
          #{$rtl} & {
            right: 50%;
            transform: translate(50%, -50%);
          }
        }
      }
    }
  }

  .code_number {
    max-width: 25%;
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
        margin-bottom: 6px;
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

  .change_password {
    font-size: 15px;
    color: $purpleColor;

    &:hover {
      font-weight: 600;
    }
  }
}

.codeNumber_menu {
  .v-list {
    &-item {
      column-gap: 5px;
    }
  }
}
</style>
