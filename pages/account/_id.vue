<template>
  <div class="my_profile">
    <div class="head">
      <h2>Personal Information</h2>
      <nuxt-link to="edit-profile" class="edit_btn">
        <img src="@/assets/img/edit-icon.svg" alt="" />
        <span>Edit</span>
      </nuxt-link>
    </div>
    <div class="peronal_informaton">
      <v-row>
        <v-col cols="12" lg="3">
          <div class="profile_pic">
            <img src="@/assets/img/profile-pic.png" alt="" />
          </div>
        </v-col>
        <v-col cols="12" lg="9">
          <div class="profile_info">
            <div class="top">
              <div class="info_box">
                <div class="tit">Name</div>
                <div class="txt">Ehsan Hassan</div>
              </div>
              <div class="info_box">
                <div class="tit">Mobile Number</div>
                <div class="txt">
                  <span>+966</span>
                  <span>24681012</span>
                </div>
              </div>
              <div class="info_box">
                <div class="tit">Email Address</div>
                <div class="txt">Ehsan@gmail.com</div>
              </div>
            </div>
            <div class="bottom">
              <div class="info_box">
                <div class="tit">About me</div>
                <div class="txt">
                  In publishing and graphic design, Lorem ipsum is a placeholder
                  text commonly used to demonstrate the visual form.
                </div>
              </div>
            </div>
          </div>
        </v-col>
      </v-row>
    </div>
    <div class="address_information">
      <div class="head">
        <h2>Address Information</h2>
        <nuxt-link to="edit-address" class="edit_btn">
          <v-icon>mdi-plus</v-icon>
          <span>Add A New Address</span>
        </nuxt-link>
      </div>
      <div class="address_info">
        <!-- <div class="no_address">You Didn’t Have Add Address Yet</div> -->
        <v-row>
          <v-col cols="12" lg="6">
            <div class="address_box">
              <div class="address_box--data">
                <v-row>
                  <v-col cols="6" md="6">
                    <div class="info_box">
                      <div class="tit">Region</div>
                      <div class="txt">Dasman</div>
                    </div>
                  </v-col>
                  <v-col cols="6" md="6">
                    <v-btn class="default_btn">Default</v-btn>
                  </v-col>
                  <v-col cols="12" md="12">
                    <div class="info_box">
                      <div class="tit">Zip Code</div>
                      <div class="txt">13111</div>
                    </div>
                  </v-col>
                  <v-col cols="12" md="12">
                    <div class="info_box">
                      <div class="tit">Street</div>
                      <div class="txt txt--address">
                        Arabian Gulf Street, Kuwait City,Flat no 3
                      </div>
                    </div>
                  </v-col>
                </v-row>
              </div>
              <div class="address_box--links">
                <nuxt-link to="edit-address">Edit</nuxt-link>
                <nuxt-link
                  to=""
                  @click.native.prevent="deleteAddress((dialog = true))"
                >
                  Remove
                </nuxt-link>
              </div>
            </div>
          </v-col>
          <v-col cols="12" lg="6">
            <div class="address_box">
              <div class="address_box--data">
                <v-row>
                  <v-col cols="6" md="6">
                    <div class="info_box">
                      <div class="tit">Region</div>
                      <div class="txt">Al Salmia</div>
                    </div>
                  </v-col>
                  <v-col cols="6" md="6">
                    <v-btn class="default_btn">Default</v-btn>
                  </v-col>
                  <v-col cols="12" md="12">
                    <div class="info_box">
                      <div class="tit">Zip Code</div>
                      <div class="txt">13111</div>
                    </div>
                  </v-col>
                  <v-col cols="12" md="12">
                    <div class="info_box">
                      <div class="tit">Street</div>
                      <div class="txt txt--address">
                        Jerssy st, 2nd floor, flat no 3
                      </div>
                    </div>
                  </v-col>
                </v-row>
              </div>
              <div class="address_box--links">
                <nuxt-link to="">Make Default</nuxt-link>
                <nuxt-link to="edit-address">Edit</nuxt-link>
                <nuxt-link
                  to=""
                  @click.native.prevent="deleteAddress((dialog = true))"
                >
                  Remove
                </nuxt-link>
              </div>
            </div>
          </v-col>
        </v-row>
      </div>
    </div>
    <!-- Delete Address Modal -->
    <DeleteAddress :openDialog="dialog" @clicked="deleteAddress" />
    <!-- Toast Message -->
    <ToastMsg
      :icon="true"
      msgTitle="Password change"
      msgContent="Your password had been changed"
    />
  </div>
</template>

<script>
import DeleteAddress from "@/components/shared/DeleteAddress";
import ToastMsg from "@/components/shared/ToastMsg";

export default {
  name: "AccountIndex",
  layout: "loggedLayout",

  components: {
    DeleteAddress,
    ToastMsg,
  },

  data() {
    return {
      dialog: false,
    };
  },

  methods: {
    deleteAddress(value) {
      this.dialog = value;
    },
  },
};
</script>

<style lang="scss">
.my_profile {
  padding-top: 16px;
  padding-inline-end: 32px;
  padding-inline-start: 15px;

  .head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 25px;

    h2 {
      font-size: 25px;
      color: #111111;
      font-family: bokraFontMedium, sans-serif;
      margin-bottom: 0;
    }

    .edit_btn {
      padding: 5px 12px;
      background-color: rgba(#e6e8ff, 0.33);
      border-radius: 2px;
      color: $greenColor;
      text-decoration: none;
      display: flex;
      align-items: center;
      justify-content: center;
      column-gap: 4px;
      border: 1px solid transparent;
      transition: 0.3s;

      .v-icon {
        font-size: 16px;
        color: $greenColor;
        font-family: bokraFontMedium, sans-serif;
      }

      span {
        font-size: 12px;
        color: $greenColor;
        font-family: bokraFontMedium, sans-serif;
        text-transform: capitalize;
      }

      &:hover {
        border-color: $greenColor;
      }
    }
  }

  .peronal_informaton {
    padding-bottom: 23px;
    border-bottom: 1px solid #e6e8ff;

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

    .profile_info {
      .top {
        display: flex;
        align-items: flex-start;
        justify-content: flex-start;
        column-gap: 40px;
        row-gap: 19px;
        margin-bottom: 19px;
      }

      .info_box {
        .tit {
          font-size: 17px;
          color: #272833;
          margin-bottom: 11px;
        }

        .txt {
          font-size: 17px;
          color: #6b6c7d;
        }
      }
    }
  }

  .address_information {
    padding-top: 24px;

    .head {
      .edit_btn {
        .v-btn__content {
          .v-icon {
            font-size: 12px;
            color: $greenColor;
            font-family: bokraFontMedium, sans-serif;
          }
        }
      }
    }

    .address_info {
      .no_address {
        padding: 150px 0;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        font-size: 16px;
        color: #989898;
      }

      .address_box {
        width: 100%;
        background-color: #f3f3ff;
        border-radius: 9px;
        padding: 20px;

        &--data {
          margin-bottom: 12px;

          .info_box {
            .tit {
              font-size: 17px;
              color: #272833;
              margin-bottom: 12px;
            }

            .txt {
              font-size: 17px;
              color: #6b6c7d;
              font-family: bokraFontLight, sans-serif;

              &--address {
                min-height: 50px;
              }
            }
          }

          .default_btn {
            @extend %btn;
            @include buttonStyle(#89b340, #fff, #89b340);
            padding: 6px 22px !important;
            border-radius: 13px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-inline-start: auto;

            .v-btn__content {
              font-size: 12px;
              text-transform: capitalize !important;
            }
          }
        }

        &--links {
          display: flex;
          align-items: center;
          justify-content: flex-end;

          a {
            font-size: 15px;
            color: $purpleColor;
            transition: 0.3s;

            &:not(:first-child) {
              margin-inline-start: 10px;
              padding-inline-start: 10px;
              border-inline-start: 1px solid #d3dce5;
            }

            &:hover {
              font-weight: 700;
            }
          }
        }
      }
    }
  }
}
</style>
