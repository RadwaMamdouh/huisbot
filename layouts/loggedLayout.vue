<template>
  <v-app dark>
    <LoggedNavbar :withBg="true" />
    <v-main>
      <div class="logged_pages_wrapper">
        <v-container>
          <BreadCrumb :breadCrumbItems="items" />
          <p class="hello_msg">
            <span>Hello Ehsan Hassan, This Is Your Basic Shop Account.</span>
            <span>
              Via The Different Options We Will Show You, You Can Modify Your
              Personal Details, View Your Orders Or Manage Your Wishlist.
            </span>
          </p>
          <div class="page_content">
            <v-row>
              <v-col cols="12" md="4" class="colBg">
                <SideBar />
              </v-col>
              <v-col cols="12" md="8" class="bgCol"><Nuxt /></v-col>
            </v-row>
          </div>
        </v-container>
      </div>
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import LoggedNavbar from "@/components/loggedNavbar/Navbar";
import BreadCrumb from "@/components/shared/BreadCrumb";
import SideBar from "@/components/shared/SideBar";
import Footer from "@/components/shared/Footer";

export default {
  components: {
    LoggedNavbar,
    BreadCrumb,
    SideBar,
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

<style lang="scss" scoped>
.logged_pages_wrapper {
  padding: 80px 0;

  .hello_msg {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-bottom: 60px;

    span {
      font-size: 14px;
      text-align: center;
    }
  }

  .page_content {
    .colBg {
      background-color: #fbfbff;
      #{$ltr} & {
        border-radius: 9px 0 0 9px;
        border-right: 1px solid #e6e8ff;
      }
      #{$rtl} & {
        border-radius: 0 9px 9px 0;
        border-left: 1px solid #e6e8ff;
      }
    }

    .bgCol {
      background-color: rgba(#f7f7ff, 0.31);
      border-radius: 7px;
    }
  }
}
</style>
