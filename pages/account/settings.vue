<template>
  <div class="my_settings">
    <h2>My Settings</h2>
    <div class="my_settings--content">
      <div class="setting_row">
        <v-checkbox label="General Subscription" hide-details></v-checkbox>
      </div>
      <div class="setting_row">
        <v-checkbox
          label="Receive email about point balance update"
          hide-details
        ></v-checkbox>
      </div>
      <div class="setting_row">
        <v-row>
          <v-col cols="12" sm="6" lg="4">
            <div class="selection">
              <h6>Repetition time</h6>
              <v-select
                :items="items"
                label="Select"
                solo
                hide-details
                :menu-props="{
                  bottom: true,
                  offsetY: true,
                  contentClass: 'time_menu',
                }"
              ></v-select>
            </div>
          </v-col>
        </v-row>
      </div>
      <div class="setting_row">
        <v-checkbox
          label="Receive Email Notifying Before Membership  Expire"
          hide-details
        ></v-checkbox>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "settings",
  layout: "loggedLayout",

  data() {
    return {
      items: ["Daily", "Weekly", "Monthly"],
    };
  },
};
</script>

<style lang="scss">
.my_settings {
  h2 {
    font-size: 25px;
    color: #111111;
    font-family: bokraFontMedium, sans-serif;
    margin-bottom: 36px;
    font-weight: 500;
  }

  &--content {
    .setting_row {
      &:not(:last-child) {
        margin-bottom: 30px;
      }

      .v-input {
        .v-input--selection-controls__input {
          .v-icon {
            color: #6c63ff !important;
            caret-color: #6c63ff !important;
          }
        }
        .v-input--selection-controls__ripple {
          &,
          &.primary--text {
            color: #6c63ff !important;
            caret-color: #6c63ff !important;
          }
        }

        &__slot {
          .v-label {
            font-size: 18px;
            color: #111111 !important;
          }
        }
      }

      .selection {
        h6 {
          font-size: 18px;
          color: #111111;
          margin-bottom: 6px;
          font-weight: 400;
        }

        .v-select {
          .v-input__control {
            .v-input__slot {
              box-shadow: none !important;
              border: 1px solid rgba(#707070, 0.1);
              border-radius: 6px;

              .v-label {
                color: #899097 !important;
                font-size: 16px;
              }

              .v-select__selections {
                .v-select__selection {
                  overflow: unset !important;
                }
              }
            }
          }
        }
      }
    }
  }
}

.time_menu {
  .v-list {
    &-item {
      &__title {
        overflow: unset !important;
      }
    }
  }
}
</style>
