<template>
      <v-app-bar
      app
      color="primary"
      dark
    >
      <a href="https://addtobasic.github.io/deadline-timer/" style="color:white;">
        <v-toolbar-title>deadline timer</v-toolbar-title>
      </a>
      <v-spacer></v-spacer>
    </v-app-bar>
</template>

<script lang="ts">
  import Vue from 'vue'
  export default Vue.extend({
    name: 'Header',
  })
</script>

<style>
  a {
    text-decoration: none;
  }
</style>
