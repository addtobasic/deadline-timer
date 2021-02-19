<template>
      <v-app-bar
      app
      color="primary"
      dark
    >
      <a href="/" style="color:white;">
        <v-toolbar-title>When is the deadline ?</v-toolbar-title>
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
