<template>
  <v-app dark>
    <Navbar />
    <v-main>
      <!-- <v-container> -->
      <Nuxt />
      <!-- </v-container> -->
    </v-main>
    <Footer />
    <!-- <span>&copy; {{ new Date().getFullYear() }}</span> -->
  </v-app>
</template>

<script>
import Navbar from "@/components/shared/Navbar";
import Footer from "@/components/shared/Footer";

export default {
  components: {
    Navbar,
    Footer,
  },
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Inspire",
          to: "/inspire",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js",
    };
  },
};
</script>
