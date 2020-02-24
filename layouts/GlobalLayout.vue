<template>
  <div id="global-layout">
    <Sidebar/>
    <MobileHeader :isOpen="isMobileHeaderOpen" @toggle-sidebar="isMobileHeaderOpen = !isMobileHeaderOpen"/>
    <div class="stream-container" @click="isMobileHeaderOpen = false">
      <BaseListLayout v-if="pagination"/>
      <div class="post-list-container post-list-container-shadow" v-else>
        <div class="post">
          <div :class="$page.frontmatter.featured_image ? 'post-head-wrapper' : 'post-head-wrapper-text-only'"
            :style="{ backgroundImage: $page.frontmatter.featured_image ? 'url(' + $page.frontmatter.featured_image + ')' : 'none' }">
            <div class="post-title">
              {{ $page.title }}
              <div class="post-meta">
                <time v-if="$page.frontmatter.date">{{ $page.frontmatter.date.match(/\d{4}-\d{2}-\d{2}/)[0] }}</time>
                <i class="material-icons" v-if="$page.frontmatter.tags">label</i>
                <NavLink class="post-meta-tag" v-for="tag in $page.frontmatter.tags" :link="'/tag/' + tag">{{ tag }}</NavLink>
              </div>
            </div>
          </div>
          <div class="post-body-wrapper">
            <div class="post-body">
              <Content/>
            </div>
          </div>
          <div class="post-comment-wrapper">
            <ClientOnly>
              <Comment v-if="disqusIdentifier" :key="$page.path" :identifier="disqusIdentifier"/>
            </ClientOnly>
          </div>
        </div>
      </div>
    </div>
    <div class="extra-container">
      <Pagination :pagination="pagination"/>
    </div>
  </div>
</template>

<script>
  import Sidebar from '@theme/components/Sidebar.vue'
  import Pagination from '@theme/components/Pagination.vue'
  import MobileHeader from '@theme/components/MobileHeader.vue'
  import { Comment } from '@vuepress/plugin-blog/lib/client/components'
  import twemoji from 'twemoji'
  import 'prismjs/themes/prism-solarizedlight.css'
  
  export default {
    components: {
      Sidebar,
      Pagination,
      MobileHeader,
      Comment,
    },

    data() {
      return {
        isMobileHeaderOpen: false
      }
    },

    computed: {
      pagination() {
        try {
          if (this.$pagination) {
            return this.$pagination
          }
        } catch (e) {}
        return undefined
      },

      $title() {
        return this.$page.title ? this.$page.title + ' - ' + this.$site.title : this.$site.title
      },

      disqusIdentifier() {
        return this.$page.id === 'post' ?
          this.$page.path :
          this.$page.path.replace(/\/$/, '.html')
      }
    },

    mounted() {
      twemoji.parse(document.body)
    }
  }
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@4.1.3/dist/css/bootstrap.min.css";
@import "https://fonts.googleapis.com/css?family=Lora|Montserrat|Material+Icons|Noto+Serif+SC:400,600";
</style>

<style lang="stylus">
@import "../styles/journal.styl"
</style>