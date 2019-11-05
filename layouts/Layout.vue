<template>
  <div>
    <BaseListLayout v-if="$pagination"/>
    <div class="post" v-else>
      <Content/>
    </div>
  </div>
</template>

<style src="prismjs/themes/prism-okaidia.css"></style>
