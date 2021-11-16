<template>
  <v-select
    v-model="select"
    :items="items"
    item-text="text"
    item-value="val"
    label="Language"
    solo
    return-object
    :menu-props="{
      bottom: true,
      offsetY: true,
      contentClass: `${landing ? 'lang_menu_landing' : 'lang_menu'} ${
        withScroll ? 'withScrollMenu' : ''
      }`,
    }"
    hide-details="true"
    prepend-inner-icon="mdi-web"
    class="lang_selection"
    :class="{ landingSelection: landing, withScroll: withScroll }"
  ></v-select>
</template>

<script>
export default {
  name: 'LangSelection',
  props: {
    landing: {
      type: Boolean,
    },
    withScroll: {
      type: Boolean,
    },
  },

  data() {
    return {
      select: { text: 'English', val: 'en' },
      items: [
        { text: 'English', val: 'en' },
        { text: 'عربي', val: 'ar' },
      ],
    }
  },
}
</script>

<style lang="scss">
.lang_selection {
  &.v-input {
    color: $purpleColor !important;
    caret-color: $purpleColor !important;

    .v-input__control {
      min-height: auto !important;
    }
    .v-input__slot {
      box-shadow: none !important;
      padding: 0 !important;

      .v-input__prepend-inner {
        #{$rtl} & {
          padding-right: 0 !important;
          padding-left: 4px !important;
        }

        .v-input__icon {
          .v-icon {
            color: $purpleColor !important;
          }
        }
      }

      .v-select__selections {
        color: $purpleColor !important;
        font-size: 14px;
        font-weight: 500;
        font-family: bokraFontMedium, sans-serif;

        .v-select__selection {
          max-width: 100% !important;
          margin: 0 !important;
          overflow: unset !important;
          font-family: bokraFontMedium, sans-serif;
        }

        input {
          width: 0;
        }
      }

      .v-input__append-inner {
        .v-input__icon {
          .v-icon {
            color: $purpleColor !important;
          }
        }
      }
    }

    &.landingSelection {
      color: #fff !important;
      caret-color: #fff !important;

      .v-input__slot {
        background-color: transparent !important;

        .v-input__prepend-inner {
          .v-input__icon {
            .v-icon {
              color: #fff !important;
            }
          }
        }

        .v-select__selections {
          color: #fff !important;
        }

        .v-input__append-inner {
          .v-input__icon {
            .v-icon {
              color: #fff !important;
            }
          }
        }
      }

      &.withScroll {
        color: #634ddc !important;
        caret-color: #634ddc !important;

        .v-input__slot {
          background-color: transparent !important;

          .v-input__prepend-inner {
            .v-input__icon {
              .v-icon {
                color: #634ddc !important;
              }
            }
          }

          .v-select__selections {
            color: #634ddc !important;
          }

          .v-input__append-inner {
            .v-input__icon {
              .v-icon {
                color: #634ddc !important;
              }
            }
          }
        }
      }
    }
  }
}

.lang_menu {
  box-shadow: none !important;
  .v-list {
    padding: 0 !important;
    box-shadow: none !important;
    background-color: rgba(#634ddc, 0.98) !important;
    backdrop-filter: brightness(15) blur(30px) opacity(0);
    border-radius: 5px !important;
    color: #fff !important;

    &-item {
      padding: 13px 20px !important;
      min-height: auto !important;
      color: #fff !important;
      font-weight: 500;
      font-family: bokraFontMedium, sans-serif;

      &.primary--text {
        color: #fff !important;
      }

      &--active {
        color: #fff !important;
        font-weight: 600;
      }

      &--highlighted {
        &::before {
          opacity: 0 !important;
        }
      }

      &__content {
        padding: 0 !important;
        overflow: unset !important;
      }

      &__title {
        overflow: unset !important;
        transition: 0.3s;
      }

      &:hover {
        .v-list-item__title {
          font-weight: 700;
        }
      }
    }
  }
}

.lang_menu_landing {
  box-shadow: none !important;
  .v-list {
    padding: 0 !important;
    box-shadow: none !important;
    background-color: rgba(#fff, 0.98) !important;
    backdrop-filter: brightness(15) blur(30px) opacity(0);
    border-radius: 5px !important;
    color: #634ddc !important;

    &-item {
      padding: 13px 20px !important;
      min-height: auto !important;
      color: #634ddc !important;
      font-weight: 500;
      font-family: bokraFontMedium, sans-serif;

      &.primary--text {
        color: #634ddc !important;
      }

      &--active {
        color: #634ddc !important;
        font-weight: 600;
      }

      &--highlighted {
        &::before {
          opacity: 0 !important;
        }
      }

      &__content {
        padding: 0 !important;
        overflow: unset !important;
      }

      &__title {
        overflow: unset !important;
        transition: 0.3s;
      }

      &:hover {
        .v-list-item__title {
          font-weight: 700;
        }
      }
    }
  }

  &.withScrollMenu {
    .v-list {
      background-color: rgba(#634ddc, 0.98) !important;

      &-item {
        color: #fff !important;

        &.primary--text {
          color: #fff !important;
        }

        &--active {
          color: #fff !important;
        }
      }
    }
  }
}
</style>
