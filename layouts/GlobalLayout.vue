<template>
  <div id="global-layout">
    <Sidebar/>
    <MobileHeader :isOpen="isMobileHeaderOpen" @toggle-sidebar="isMobileHeaderOpen = !isMobileHeaderOpen"/>
    <div class="stream-container" @click="isMobileHeaderOpen = false">
      <div class="post-list-container">
        <DefaultGlobalLayout/>
      </div>
    </div>
  </div>
</template>

<script>
  import GlobalLayout from '@app/components/GlobalLayout.vue'
  import Sidebar from '@theme/components/Sidebar.vue'
  import MobileHeader from '@theme/components/MobileHeader.vue'
  import Footer from '@theme/components/Footer.vue'

  export default {
    components: {
      DefaultGlobalLayout: GlobalLayout,
      Sidebar,
      MobileHeader,
      Footer
    },

    data() {
      return {
        isMobileHeaderOpen: false
      }
    },

    mounted() {
      this.$router.afterEach(()=>{
        this.isMobileHeaderOpen = false
      })
    }
  }
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@4.1.3/dist/css/bootstrap.min.css";
</style>

<style lang="stylus">
@import "../styles/journal.styl"
</style>