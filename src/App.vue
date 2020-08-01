<template>
  <div id="app">
    <v-app>

      <Header></Header>
      <Meigen></Meigen>
      <Footer></Footer>
    </v-app>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import Header from './components/Header.vue';
  import Footer from './components/Footer.vue';
  import Meigen from './components/Meigen.vue';
  export default Vue.extend({
    name: 'App',

    components: {
      Header,
      Footer,
      Meigen,
    },

    data: () => ({
      //
    }),
  });
</script>
