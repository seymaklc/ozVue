<template>
  <div class="wrapper">
    <side-bar>
      <template slot="links">
        <sidebar-link to="/dashboard" name="File Upload" icon="ti-upload" />
        <sidebar-link to="/stats" name="Ref. Network File Upload" icon="ti-upload" />
        <sidebar-link to="/typography" name="Parameters" icon="ti-panel" />
        <sidebar-link to="/icons" name="Outputs" icon="ti-pie-chart" />
        <sidebar-link to="/maps" name="Download" icon="ti-download" />
        <sidebar-link to="/notifications" name="Github" icon="ti-github" />
        <!--        <sidebar-link-->
        <!--          to="/table-list"-->
        <!--          name="Table List"-->
        <!--          icon="ti-view-list-alt"-->
        <!--        />-->
      </template>
      <mobile-menu>
        <li class="nav-item">
          <a class="nav-link">
            <i class="ti-panel"></i>
            <p>Stats</p>
          </a>
        </li>
        <drop-down
          class="nav-item"
          title="5 Notifications"
          title-classes="nav-link"
          icon="ti-bell"
        >
          <a class="dropdown-item">Notification 1</a>
          <a class="dropdown-item">Notification 2</a>
          <a class="dropdown-item">Notification 3</a>
          <a class="dropdown-item">Notification 4</a>
          <a class="dropdown-item">Another notification</a>
        </drop-down>
        <li class="nav-item">
          <a class="nav-link">
            <i class="ti-settings"></i>
            <p>Settings</p>
          </a>
        </li>
        <li class="divider"></li>
      </mobile-menu>
    </side-bar>
    <div class="main-panel">
      <top-navbar></top-navbar>

      <dashboard-content @click.native="toggleSidebar"> </dashboard-content>

      <content-footer></content-footer>
    </div>
  </div>
</template>
<style lang="scss"></style>
<script>
import TopNavbar from "./TopNavbar.vue";
import ContentFooter from "./ContentFooter.vue";
import DashboardContent from "./Content.vue";
import MobileMenu from "./MobileMenu";
export default {
  components: {
    TopNavbar,
    ContentFooter,
    DashboardContent,
    MobileMenu,
  },
  methods: {
    toggleSidebar() {
      if (this.$sidebar.showSidebar) {
        this.$sidebar.displaySidebar(false);
      }
    },
  },
};
</script>
