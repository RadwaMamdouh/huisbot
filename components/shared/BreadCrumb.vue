<template>
  <v-breadcrumbs
    :items="breadCrumbItems"
    divider="."
    tag="span"
  ></v-breadcrumbs>
</template>

<script>
export default {
  name: "BreadCrumb",

  props: {
    breadCrumbItems: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {};
  },
};
</script>

<style lang="scss">
.v-breadcrumbs {
  padding: 0 !important;
  margin-bottom: 22px;

  &__item {
    font-size: 12px;
    color: #343a40 !important;
  }

  &__divider {
    font-size: 0 !important;
    width: 3px;
    height: 3px;
    border-radius: 100%;
    padding: 0 !important;
    margin: 0 7px;
    background-color: #343a40;
  }
}
</style>
