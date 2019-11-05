<template>
  <div class="post">
    <div class="post-body-wrapper">
      <Content/>
    </div>
    <div class="post-comment-wrapper">
      <Comment/>
    </div>
  </div>
</template>

<script>
  import Toc from '@theme/components/Toc.vue'
  import { Comment } from '@vuepress/plugin-blog/lib/client/components'
  
  export default {
    components: {
      Toc,
      Comment,
    },
  }
</script>

<style src="prismjs/themes/prism-okaidia.css"></style>

