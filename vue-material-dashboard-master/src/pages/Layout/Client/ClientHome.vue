<template>
    <div>
      <top-navbar></top-navbar>

      <fixed-plugin
        :color.sync="sidebarBackground"
        :image.sync="sidebarBackgroundImage"
      >
      </fixed-plugin>

      <dashboard-content> </dashboard-content>

      <content-footer v-if="!$route.meta.hideFooter"></content-footer>
    </div>

</template>

<script>
import TopNavbar from "../TopNavbar.vue";
import ContentFooter from "../ContentFooter.vue";
import DashboardContent from "../Content.vue";
import FixedPlugin from "../Extra/FixedPlugin.vue";

export default {
  components: {
    TopNavbar,
    DashboardContent,
    ContentFooter,
    FixedPlugin
  },
  data() {
    return {
      sidebarBackground: "green",
      sidebarBackgroundImage: require("@/assets/img/sidebar-2.jpg")
    };
  }
};
</script>
