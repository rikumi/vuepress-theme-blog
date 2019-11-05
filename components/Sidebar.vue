<template>
  <section class="side-container">
    <header>
      <NavLink link="/" class="a-block nav-head">
        <div class="nav-title">
          {{ $site.title }}
        </div>
        <div class="nav-subtitle">
          {{ $site.subtitle }}
        </div>
      </NavLink>
      <ul class="nav-link-list" v-if="$themeConfig.nav">
        <NavLink :link="item.link" class="a-block nav-link-item" v-for="item in $themeConfig.nav">
          {{ item.text }}
        </NavLink>
      </ul>
    </header>
    <footer class="nav-footer">
      <!-- <NavLink :link="item.link">{{ item.text }}</NavLink> -->
    </footer>
  </section>
</template>

<script>
  import SearchBox from '@SearchBox'

  export default {
    components: { SearchBox },
  }
</script>
