<template>
  <div class="pagination" v-if="pagination">
    <a id="globalBackToTop" href="#top" class="pagination-action animated-visibility invisible">
      <i class="material-icons pagination-action-icon">keyboard_arrow_up</i>
    </a>
    <div class="pagination-indicator">
      <span style="text-align: center;">
        {{ pagination.paginationIndex + 1 }}
        <br>
        <div style="display: inline-block; transform: rotate(-28deg);">-</div>
        <br>
        {{ pagination._paginationPages.length }}
      </span>
    </div>
    <router-link class="pagination-action" v-if="pagination.hasPrev" :to="pagination.prevLink">
      <i class="material-icons pagination-action-icon">chevron_left</i>
    </router-link>
    <router-link class="pagination-action" v-if="pagination.hasNext" :to="pagination.nextLink">
      <i class="material-icons pagination-action-icon">chevron_right</i>
    </router-link>
  </div>
</template>

<script>
  export default {
    props: ['pagination']
  }
</script>
