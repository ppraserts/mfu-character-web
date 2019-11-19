<template>
  <!-- Main Sidebar Container -->
  <aside class="main-sidebar sidebar-dark-primary elevation-4">
    <!-- Brand Logo -->
    <a href="index3.html" class="brand-link">
      <img
        src="dist/img/AdminLTELogo.png"
        alt="AdminLTE Logo"
        class="brand-image img-circle elevation-3"
        style="opacity: .8"
      >
      <span class="brand-text font-weight-light">AdminLTE 3</span>
    </a>

    <!-- Sidebar -->
    <div class="sidebar">
      <!-- Sidebar user panel (optional) -->
      <div class="user-panel mt-3 pb-3 mb-3 d-flex">
        <div class="image">
          <img src="dist/img/user2-160x160.jpg" class="img-circle elevation-2" alt="User Image">
        </div>
        <div class="info">
          <a href="#" class="d-block">Alexander Pierce</a>
        </div>
      </div>

      <!-- Sidebar Menu -->
      <nav class="mt-2">
        <ul class="nav nav-pills nav-sidebar flex-column" data-widget="treeview" role="menu" data-accordion="false">
          <!-- Add icons to the links using the .nav-icon class
               with font-awesome or any other icon font library -->
          <li v-for="sideBar in sideBarList" v-bind:key="sideBar.id" v-bind:class="sideBar.class">
            <a class="nav-link" v-bind:class="{ 'active': sideBar.isActive }" v-bind:href="sideBar.href">
              <i class="nav-icon fas fa-tachometer-alt" />
              <p>
                {{ sideBar.title }}
                <i v-if="sideBar.subSideBars !== undefined" class="right fas fa-angle-left" />
              </p>
            </a>
            <ul v-if="sideBar.subSideBars !== undefined" class="nav nav-treeview">
              <li v-for="subSideBar in sideBar.subSideBars" v-bind:key="subSideBar.id" class="nav-item">
                <a class="nav-link" v-bind:class="{ 'active': subSideBar.isActive }" v-bind:href="subSideBar.href">
                  <i class="far fa-circle nav-icon" />
                  <p>{{ subSideBar.title }}</p>
                </a>
              </li>
            </ul>
          </li>
        </ul>
      </nav>
      <!-- /.sidebar-menu -->
    </div>
    <!-- /.sidebar -->
  </aside>
</template>

<script>
export default {
    mounted() {
       
    },
    computed: {
        sideBarList() {
            let url = window.location.href;
            let param = url.split("?")[1];
            let sideBarList = []

            sideBarList.push({
                        id: 1,
                        title: "Dashboard",
                        icon: "nav-icon fas fa-tachometer-alt",
                        class: "nav-item has-treeview",
                        isActive: false,
                        subSideBars: [{
                            id: 11,
                            title: "Dashboard v1",
                            isActive: true,
                            href: "#"
                        },
                        {
                            id: 12,
                            title: "Dashboard v2",
                            isActive: false,
                            href: "#"
                        }],
                        href: "#"
                    });

            if(param==="admin") {
                sideBarList.push({
                        id: 2,
                        title: "Admin",
                        icon: "nav-icon fas fa-tachometer-alt",
                        class: "nav-item",
                        isActive: false,
                        href: "#"
                    });
            } else {
                sideBarList.push({
                        id: 2,
                        title: "User",
                        icon: "nav-icon fas fa-tachometer-alt",
                        class: "nav-item",
                        isActive: false,
                        href: "#"
                    });
                
                 sideBarList.push({
                        id: 3,
                        title: "Chart",
                        icon: "nav-icon fas fa-tachometer-alt",
                        class: "nav-item has-treeview",
                        isActive: false,
                        subSideBars: [{
                            id: 31,
                            title: "Chart v1",
                            isActive: false,
                            href: "#"
                        },
                        {
                            id: 32,
                            title: "Chart v2",
                            isActive: false,
                            href: "#"
                        }],
                        href: "#"
                    });
            }

            sideBarList.push({
                        id: 999,
                        title: "Logout",
                        icon: "nav-icon fas fa-tachometer-alt",
                        class: "nav-item",
                        isActive: false,
                        href: "/login"
            });

            return sideBarList;
        }
    }
}
</script>
