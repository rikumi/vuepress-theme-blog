<template>
  <div class="pagination" v-if="pagination">
    <a id="globalBackToTop" href="#top" class="pagination-action animated-visibility invisible">
      <i class="material-icons pagination-action-icon">keyboard_arrow_up</i>
    </a>
    <router-link class="pagination-action" v-if="pagination.hasPrev" :to="pagination.prevLink">
      <i class="material-icons pagination-action-icon">chevron_left</i>
    </router-link>
    <div class="pagination-indicator">
      <span style="text-align: center;">
        {{ pagination.paginationIndex + 1 }}
        <br>
        <div style="display: inline-block; transform: rotate(-28deg);">-</div>
        <br>
        {{ pagination._paginationPages.length }}
      </span>
    </div>
    <router-link class="pagination-action" v-if="pagination.hasNext" :to="pagination.nextLink">
      <i class="material-icons pagination-action-icon">chevron_right</i>
    </router-link>
    <div class="pagination-action" @click="toggleDarkMode">
      <i
        class="material-icons pagination-action-icon pagination-action-icon-small"
      >{{ isDarkMode ? 'wb_sunny' : 'brightness_2' }}</i>
    </div>
  </div>
</template>

<script>
export default {
  props: ['pagination'],
  data() {
    return {
      isDarkMode: false
    };
  },
  mounted() {
    this.isDarkMode = !!+(
      localStorage.getItem('vuepress-theme-journal-dark-mode') ||
      window.matchMedia('(prefers-color-scheme: dark)').matches
    );
  },
  methods: {
    toggleDarkMode() {
      if (this.isDarkMode) {
        localStorage.setItem('vuepress-theme-journal-dark-mode', '0');
        location.reload();
      } else {
        localStorage.setItem('vuepress-theme-journal-dark-mode', '1');
        location.reload();
      }
    }
  }
};
</script>
