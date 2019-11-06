<template>
  <section class="side-container">
    <header>
      <NavLink link="/" class="a-block nav-head" :class="{ active: $route.path === '/' }">
        <div class="nav-title">{{ $site.title }}</div>
        <div class="nav-subtitle">{{ $site.description }}</div>
      </NavLink>

      <ul class="nav-link-list" v-if="$themeConfig.nav">
        <NavLink
          :link="item.link"
          class="a-block nav-link-item"
          v-for="item in $themeConfig.nav"
          :class="{ active: $route.path === item.link }"
        >{{ item.text }}</NavLink>
      </ul>
    </header>
    <footer class="nav-footer">
      Proudly published with VuePress
      <br />Theme
      <a
        href="https://github.com/rikumi/vuepress-theme-journal/"
        target="_blank"
        rel="noreferrer noopener"
      >Journal.</a> by
      <a href="https://github.com/rikumi/" target="_blank" rel="noreferrer noopener">Rikumi</a>
      <br />Designed by
      <a href="https://mak1t0.cc/" target="_blank" rel="noreferrer noopener">Makito</a>
      <br />
      © {{ new Date().getFullYear() }}
      <NavLink link="/">{{ $site.title }}</NavLink>
    </footer>
  </section>
</template>
