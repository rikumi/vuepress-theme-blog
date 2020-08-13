<template>
  <div class="mobile-header">
    <div
      class="single-column-drawer-container"
      :class="{ 'single-column-drawer-container-active': isOpen }"
    >
      <div class="drawer-content">
        <div class="drawer-menu">
          <NavLink
            :link="item.link"
            class="a-block drawer-menu-item"
            v-for="item in $themeConfig.nav"
            :class="{ active: $route.path === item.link }"
          >{{ item.text }}</NavLink>
        </div>
      </div>
    </div>
    <div class="navbar navbar-light single-column-nav-container">
      <div class="nav-background"></div>
      <div class="container container-narrow nav-content">
        <button
          id="nav_dropdown_btn"
          type="button"
          class="nav-dropdown-toggle"
          @click="$emit('toggle-sidebar')"
        >
          <i class="material-icons">menu</i>
        </button>
        <NavLink link="/" class="navbar-brand">{{ $site.title }}</NavLink>
      </div>
    </div>
    <div class="single-column-drawer-mask" v-if="isOpen" @click="$emit('toggle-sidebar')"></div>
  </div>
</template>

<script>
import { MenuIcon, XIcon } from 'vue-feather-icons';

export default {
  props: {
    isOpen: {
      type: Boolean,
      required: true
    }
  },

  components: {
    MenuIcon,
    XIcon
  }
};
</script>
