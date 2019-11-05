<template>
  <div class="single-column-header-container">
    <div class="mobile-header-bar">
      <div class="mobile-header-title">
        <NavLink
          link="/"
          class="mobile-home-link"
        >{{ $site.title }}
        </NavLink>
        <component :is="isOpen ? 'XIcon' : 'MenuIcon'" @click="$emit('toggle-sidebar')"/>
      </div>
      <div class="mobile-menu-wrapper" v-bind:class="{ open: isOpen }">
        <hr class="menu-divider"/>
        <ul class="mobile-nav" v-if="$themeConfig.nav">
          <li class="mobile-nav-item" v-for="item in $themeConfig.nav">
            <NavLink :link="item.link">{{ item.text }}</NavLink>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  import {
    MenuIcon,
    XIcon
  } from 'vue-feather-icons'

  export default {
    props:{
      isOpen:{
        type: Boolean,
        required: true
      }
    },

    components: {
      MenuIcon,
      XIcon
    },
}
</script>
