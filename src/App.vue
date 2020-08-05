<template>
  <div id="app">
    <v-app dark>
      <Header></Header>
      <v-main>
        <Main></Main>
      </v-main>
      <Footer></Footer>
    </v-app>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import Header from './components/Header.vue';
  import Footer from './components/Footer.vue';
  import Main from './components/Main.vue';
  import Meigen from './components/Meigen.vue';

  export default Vue.extend({
    name: 'App',
    components: {
      Header,
      Footer,
      Main,
      Meigen,
    },
  });
</script>
