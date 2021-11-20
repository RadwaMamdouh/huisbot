<template>
  <div class="my_properties">
    <h2>Properties preferences</h2>
    <div class="properties_content">
      <v-row>
        <v-col cols="12" md="6">
          <!-- Property type -->
          <div class="property_box">
            <h6>Property type</h6>
            <div class="input_holder">
              <v-text-field
                v-model="property"
                solo
                label="Search For Type"
                clearable
                append-icon="mdi-magnify"
                class="search_input"
                hide-details
              ></v-text-field>
            </div>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Apartment</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>House</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Land</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Studio</span>
              </label>
            </div>
          </div>

          <!-- Location -->
          <div class="property_box">
            <h6>Location</h6>
            <div class="input_holder">
              <v-text-field
                v-model="city"
                solo
                label="City"
                clearable
                append-icon="mdi-magnify"
                class="search_input"
                hide-details
              ></v-text-field>
            </div>
            <div class="input_holder">
              <v-text-field
                v-model="country"
                solo
                label="Country"
                clearable
                append-icon="mdi-magnify"
                class="search_input"
                hide-details
              ></v-text-field>
            </div>
          </div>

          <!-- Price -->
          <div class="property_box price">
            <h6>Price</h6>
            <div class="price_range">
              <v-range-slider
                v-model="range"
                :max="max"
                :min="min"
                hide-details
                class="align-center"
                :color="`#142461`"
                thumb-label="always"
              >
                <template v-slot:thumb-label="{ value }">
                  $ {{ value }}
                </template>
              </v-range-slider>
              <div class="min_max">
                <v-row>
                  <v-col cols="6" md="6">
                    <h5>Min</h5>
                    <v-text-field
                      :value="range[0]"
                      class="mt-0 pt-0"
                      hide-details
                      single-line
                      type="number"
                      style="width: 100%"
                      disabled
                      @change="$set(range, 0, $event)"
                    >
                      <template v-slot:prepend-inner>
                        <span>$</span>
                      </template>
                    </v-text-field>
                  </v-col>
                  <v-col cols="6" md="6">
                    <h5>Max</h5>
                    <v-text-field
                      :value="range[1]"
                      class="mt-0 pt-0"
                      hide-details
                      single-line
                      type="number"
                      style="width: 100%"
                      disabled
                      @change="$set(range, 1, $event)"
                    >
                      <template v-slot:prepend-inner>
                        <span>$</span>
                      </template>
                    </v-text-field>
                  </v-col>
                </v-row>
              </div>
            </div>
          </div>

          <!-- Bedroom -->
          <div class="property_box">
            <h6>Bedroom</h6>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>1</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>2</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>3</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>4</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>+5</span>
              </label>
            </div>
          </div>

          <!-- Amenities -->
          <div class="property_box">
            <h6>Amenities</h6>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Dishwasher</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Washing machine</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Dryer</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Air conditioning</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Heating</span>
              </label>
            </div>
          </div>
        </v-col>
        <v-col cols="12" md="6" class="colBorder">
          <!-- Neighnourhood -->
          <div class="property_box">
            <h6>Neighnourhood</h6>
            <div class="input_holder">
              <v-text-field
                v-model="property"
                solo
                label="Search For Type"
                clearable
                append-icon="mdi-magnify"
                class="search_input"
                hide-details
              ></v-text-field>
            </div>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Neighnourhood1</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Neighnourhood2</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Neighnourhood3</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Neighnourhood4</span>
              </label>
            </div>
          </div>

          <!-- Furniture -->
          <div class="property_box">
            <h6>Furniture</h6>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Furnished</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Unfurnished</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Shell</span>
              </label>
            </div>
          </div>

          <!-- Facilities -->
          <div class="property_box">
            <h6>Facilities</h6>
            <div class="checkboxes">
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Private bathroom</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Balcony/Terrace</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Garden</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Kitchen</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Pets allowed</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Parking</span>
              </label>
              <label class="custom_checkbox">
                <input type="checkbox" class="d-none" />
                <v-icon>mdi-check</v-icon>
                <span>Basement</span>
              </label>
            </div>
          </div>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
export default {
  name: "properties",
  layout: "loggedLayout",

  data() {
    return {
      property: "",
      city: "",
      country: "",
      min: 0,
      max: 90,
      range: [20, 70],
    };
  },
};
</script>

<style lang="scss">
.my_properties {
  h2 {
    font-size: 25px;
    color: #111111;
    font-family: bokraFontMedium, sans-serif;
    margin-bottom: 32px;
    font-weight: 500;
  }

  .properties_content {
    .colBorder {
      border-inline-start: 1px solid #ebedf5;
    }

    .property_box {
      margin-bottom: 60px;

      h6 {
        font-size: 14px;
        color: #111111;
        font-family: bokraFontMedium, sans-serif;
        margin-bottom: 10px;
        font-weight: 500;
      }

      .input_holder {
        margin-bottom: 14px;

        .search_input {
          .v-input {
            &__slot {
              box-shadow: none !important;
              border: 1px solid #ebedf5;
              border-radius: 3px;

              .v-label {
                font-size: 12px;
                color: #111111 !important;
              }
            }

            &__icon {
              .v-icon {
                color: #304659;
              }
            }
          }
        }
      }

      .checkboxes {
        margin-bottom: 38px;

        .custom_checkbox {
          &:not(:last-child) {
            margin-bottom: 16px;
          }

          display: flex;
          align-items: flex-start;
          justify-content: flex-start;
          column-gap: 8px;
          cursor: pointer;
          width: fit-content;

          .v-icon {
            width: 24px;
            height: 24px;
            padding: 2px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0 0 2px rgba($purpleColor, 0.4);
            color: transparent;
            transition: 0.3s;
          }

          span {
            font-size: 12px;
            color: #111111;
            margin-top: 3px;
          }

          input:checked ~ .v-icon {
            color: $greenColor;
          }
        }
      }

      &.price {
        h6 {
          margin-bottom: 22px;
        }

        .price_range {
          .v-input {
            &__slider {
              .v-slider__thumb {
                width: 3px;
                height: 12px;
                left: -3px;
                border-radius: 5px;

                &::before {
                  width: 26px;
                  height: 26px;
                  top: -8px;
                }

                &::after {
                  width: 20px;
                  height: 20px;
                }

                &-label {
                  top: 100% !important;
                  bottom: 0 !important;
                  transform: translateY(0) translateY(10px) translateX(-50%)
                    rotate(45deg) !important;
                  background-color: transparent !important;
                  border-color: transparent !important;
                  font-size: 12px;
                  color: #111111;
                }
              }

              .v-slider__track-background {
                background-color: #caccce !important;
                border-color: #caccce !important;
              }
            }
          }
          .min_max {
            margin-top: 47px;

            h5 {
              font-size: 14px;
              margin-bottom: 9px;
              color: #111111;
              font-weight: 400;
            }

            .v-input {
              &__slot {
                background-color: #fff;
                border: 1px solid #ebedf5;
                border-radius: 3px;
                padding: 8px 16px;

                &::before,
                &::after {
                  display: none !important;
                }
              }

              &__prepend-inner {
                align-self: center !important;
                margin-top: 0;
                font-size: 12px;
                color: #111111;
              }

              .v-text-field__slot {
                input {
                  font-size: 12px;
                  color: #111111;
                }
              }
            }
          }
        }
      }
    }
  }
}
</style>
