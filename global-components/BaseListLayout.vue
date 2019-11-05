<template>
    <div class="ui-posts">
      <div class="post-item-wrapper" v-for="page in pages">
        <NavLink :link="page.path">
          <div class="post-item">
            <div class="post-item-info-wrapper">
              <div class="post-item-title">
                {{ page.title }}
              </div>
              
              <div class="post-item-summary">
                {{ page.frontmatter.summary || page.summary }}
                <!-- <Content :page-key="page.key" slot-key="intro"/>-->
              </div>

              <div class="post-item-meta" v-if="page.frontmatter.author">
                <span>{{ resovlePostDate(page.frontmatter.date) }}</span>
              </div>
            </div>
          </div>
        </NavLink>
      </div>
      <component v-if="$pagination.length > 1 && paginationComponent" :is="paginationComponent"></component>
    </div>
</template>

<script>
  /* global THEME_BLOG_PAGINATION_COMPONENT */
  
  import Vue from 'vue'
  import { NavigationIcon, ClockIcon } from 'vue-feather-icons'
  import { Pagination, SimplePagination } from '@vuepress/plugin-blog/lib/client/components'
  
  export default {
    components: { NavigationIcon, ClockIcon },

    data() {
      return {
        paginationComponent: null
      }
    },
    
    created() {
      this.paginationComponent = this.getPaginationComponent()
    },
    
    computed: {
      pages() {
        return this.$pagination.pages
      },
    },
    
    methods: {
      getPaginationComponent() {
        const n = THEME_BLOG_PAGINATION_COMPONENT
        if (n === 'Pagination') {
          return Pagination
        }

        if (n === 'SimplePagination') {
          return SimplePagination
        }

        return Vue.component(n) || Pagination
      },

      resovlePostDate(date) {
        return new Date(date.replace(/\-/g, "/").trim()).toDateString()
      }
    }
  }
</script>

<style src="prismjs/themes/prism-okaidia.css"></style>


