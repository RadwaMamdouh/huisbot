<template>
  <div class="sideBar_wrapper">
    <ul>
      <li>
        <nuxt-link to="/account/profile">
          <div class="top">
            <div class="icon">
              <img src="@/assets/img/profile.svg" alt="" />
            </div>
            <div class="p_name">My Profile</div>
          </div>
          <div class="p_desc">Review Your Personal Information</div>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/account/properties">
          <div class="top">
            <div class="icon">
              <img src="@/assets/img/properties.svg" alt="" />
            </div>
            <div class="p_name">My Properties</div>
          </div>
          <div class="p_desc">You Can Type Here Any Text</div>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/account/payment">
          <div class="top">
            <div class="icon">
              <img src="@/assets/img/payment.svg" alt="" />
            </div>
            <div class="p_name">Payment</div>
          </div>
          <div class="p_desc">You Can Type Here Any Text</div>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/account/points">
          <div class="top">
            <div class="icon">
              <img src="@/assets/img/my-points.svg" alt="" />
            </div>
            <div class="p_name">My Points</div>
          </div>
          <div class="p_desc">You Can Type Here Any Text</div>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/account/settings">
          <div class="top">
            <div class="icon">
              <img src="@/assets/img/settings.svg" alt="" />
            </div>
            <div class="p_name">My Settings</div>
          </div>
          <div class="p_desc">You Can Type Here Any Text</div>
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
};
</script>

<style lang="scss" scoped>
.sideBar_wrapper {
  padding: 18px 50px 274px;

  @media (max-width: 1264.98px) {
    padding: 18px 10px 274px;
  }

  @media (max-width: 960.98px) {
    padding: 18px 50px 50px;
  }

  ul {
    list-style: none !important;
    padding: 0 !important;

    li {
      &:not(:last-child) {
        a {
          margin-bottom: 19px;
          padding-bottom: 19px;
          border-bottom: 1px solid #e6e8ff;
        }
      }

      a {
        display: flex;
        align-items: flex-start;
        justify-content: flex-start;
        flex-direction: column;
        text-decoration: none;
        row-gap: 5px;

        .top {
          display: flex;
          align-items: center;
          justify-content: flex-start;
          column-gap: 8px;

          .icon {
            width: 32px;
            height: 32px;
            border-radius: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #e6e8ff;
            padding: 2px;
          }

          .p_name {
            font-size: 18px;
            color: #313131;
            font-family: bokraFontMedium, sans-serif;
            font-weight: 500;
            transition: 0.3s;
          }
        }

        .p_desc {
          font-size: 14px;
          color: #313131;
          font-family: bokraFontLight, sans-serif;
          font-weight: 300;
        }

        &.nuxt-link-exact-active,
        &:hover {
          .top {
            .p_name {
              color: $purpleColor;
            }
          }
        }
      }
    }
  }
}
</style>
