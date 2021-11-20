<template>
  <v-app dark>
    <LoggedNavbar :withBg="true" />
    <v-main>
      <Nuxt />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import LoggedNavbar from "@/components/loggedNavbar/Navbar";
import Footer from "@/components/shared/Footer";

export default {
  components: {
    LoggedNavbar,
    Footer,
  },

  data() {
    return {
      items: [
        {
          text: "Home",
          disabled: false,
          href: "/",
        },
        {
          text: "Profile Page",
          disabled: true,
          href: "/account/",
        },
      ],
    };
  },
};
</script>
