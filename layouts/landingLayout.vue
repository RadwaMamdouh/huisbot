<template>
  <v-app dark>
    <!-- <Navbar /> -->
    <LoggedNavbar />
    <v-main>
      <Nuxt />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Navbar from "@/components/landing/Navbar";
import LoggedNavbar from "@/components/loggedNavbar/Navbar";
import Footer from "@/components/shared/Footer";

export default {
  components: {
    Navbar,
    LoggedNavbar,
    Footer,
  },
};
</script>
