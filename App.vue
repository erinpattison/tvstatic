<template>
  <header>
    <Header />
  </header>
  
  <RouterView />

  <footer>
    <Footer />
  </footer>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import { RouterView } from "vue-router";
export default {
  components: {
    Header: Header,
    Footer: Footer,
    RouterView: RouterView,
  },
};
</script>
<style>
@import "./assets/base.css";
</style>
