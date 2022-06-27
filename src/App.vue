<template>
  <div id=" app">
    <HeaderNav />

    <div v-if="$route.path == '/'">
      <!-- if the route is this one  / -->

      <h1 class="pt-5 font-weight-light">
        Vos films préférés sont sur Happy Movies!
      </h1>

      <MoviesList :movies="movies" :loading="loading" :errored="errored" />
    </div>

    <div v-else>
      <!-- if the route is not this one  / -->

      <router-view v-bind:key="$route.fullPath"></router-view>
    </div>

    <FooterSite />
  </div>
</template>


<script>

import HeaderNav from "./components/template/HeaderNav.vue";
import FooterSite from "./components/template/FooterSite.vue";

export default {
  name: "App",
  components: {
    HeaderNav,
    FooterSite,
  },
};
</script>

<style>
</style>
