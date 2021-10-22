<template>
    <v-footer
      :absolute="!fixed"
      app
      color="primary"
      dark
    >
      <div>つくったひと <a href="https://twitter.com/addtobasic" target="_blank" style="color:white;">げんし</a></div>
      <div class="flex-grow-1"></div>
      <div><v-icon>mdi-gmail</v-icon>addtobasic@gmail.com</div>
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
