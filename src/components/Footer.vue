<template>
    <v-footer
      :absolute="!fixed"
      app
      color="#44bc84"
      dark
    >
      <div class="flex-grow-1"></div>
      <v-icon>mdi-gmail</v-icon>
      genshi0916@gmail.com
    </v-footer>
</template>

<script lang="ts">
  import Vue from 'vue'
  export default Vue.extend({
    name: 'Footer',

  })
</script>
<style>
#gmail{
  margin-right:3px;
}
</style>
