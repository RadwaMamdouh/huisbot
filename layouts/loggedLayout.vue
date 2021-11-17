<template>
  <v-app dark>
    <Navbar />
    <v-main>
      <Nuxt />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Navbar from "@/components/landing/Navbar";
import Footer from "@/components/shared/Footer";

export default {
  components: {
    Navbar,
    Footer,
  },
};
</script>
