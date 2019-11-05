<template>
  <div class="post-list-container post-list-container-no-background">
    <NavLink class="a-block" :link="page.path" v-for="page in pages">
      <div class="post-item-wrapper">
        <div class="post-item">
          <div class="post-item-info-wrapper">
            <div class="post-item-title">
              {{ page.title }}
            </div>
            
            <div class="post-item-summary">
              {{ (page.frontmatter.summary || page.summary || '').replace(/<.*?(>|$)/g, '') }}
              <!-- <Content :page-key="page.key" slot-key="intro"/>-->
            </div>

            <div class="post-item-meta">
              <span>{{ page.frontmatter.date.toString().match(/\d{4}-\d{2}-\d{2}/)[0] }}</span>
            </div>
          </div>
          <div class="post-item-image-wrapper" v-if="page.frontmatter.featured_image">
            <div class="post-item-image" :style="{ backgroundImage: 'url(' + page.frontmatter.featured_image + ')' }"></div>
          </div>
        </div>
      </div>
    </NavLink>
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
      }
    }
  }
</script>

