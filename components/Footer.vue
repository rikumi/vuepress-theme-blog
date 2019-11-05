<template>
</template>

<script>
  import {
    GithubIcon,
    FacebookIcon,
    TwitterIcon,
    InstagramIcon,
    LinkedinIcon
  } from 'vue-feather-icons'
  
  export default {
    components: {
      GithubIcon,
      FacebookIcon,
      TwitterIcon,
      InstagramIcon,
      LinkedinIcon
    },
    
    methods: {
      getIconComponentName(contactType) {
        switch (contactType) {
          case 'github':
            return 'GithubIcon'
          case 'facebook':
            return 'FacebookIcon'
          case 'twitter':
            return 'TwitterIcon'
          case 'instagram':
            return 'InstagramIcon'
          case 'linkedin':
            return 'LinkedinIcon'
          default:
            return ''
        }
      },
    },
    
    computed: {
      contact() {
        return (
          this.$themeConfig.footer && this.$themeConfig.footer.contact || []
        )
          .map(({ type, link }) => {
            return {
              iconComponent: this.getIconComponentName(type),
              link,
            }
          })
          .filter(({ iconComponent }) => iconComponent)
      },
      
      copyright() {
        return (
          this.$themeConfig.footer && this.$themeConfig.footer.copyright || []
        )
      },
    },
  }
</script>
