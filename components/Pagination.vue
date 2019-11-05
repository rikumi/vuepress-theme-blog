<template>
  <div
    class="pagination"
    v-if="pagination"
  >
    <router-link
      class="prev"
      title="Previous Page"
      v-if="pagination.hasPrev"
      :to="pagination.prevLink"
    >
      Prev
    </router-link>
    <router-link
      class="next"
      title="Next Page"
      v-if="pagination.hasNext"
      :to="pagination.nextLink"
    >
      Next
    </router-link>
  </div>
</template>

<script>
  export default {
    props: ['pagination']
  }
</script>
