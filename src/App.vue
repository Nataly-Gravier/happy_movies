<template>
  <div id=" app">
    <HeaderNav />

    <div v-if="$route.path == '/'">
      <!-- if the route is this one  / -->

      <h1 class="pt-5 font-weight-light">
        Vos films préférés sont sur Happy Movies!
      </h1>

      <MovieList :movies="movies" :loading="loading" :errored="errored" />

    </div>

    <div v-else>
      <!-- if the route is not this one  / -->

      <router-view v-bind:key="$route.fullPath"></router-view>
    </div>

    <FooterSite />

  </div>


</template>


<script>

import HeaderNav from "./components/template/HeaderNav.vue"
import FooterSite from "./components/template/FooterSite.vue"
import axios from "axios"
import MovieList from "./components/utils/MovieList.vue"

export default {
  name: "App",
  components: {
    HeaderNav,
    FooterSite,
    MovieList,
  },

  data() {
    return {
      movies: null
    }
  },

  created() {
    axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1")
      .then((firstAPIresponse) => {
        this.movies = firstAPIresponse.data.results;
        console.log(this.movies)

        axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=2")
          .then((secondAPIresponse) => {

            secondAPIresponse.data.results.forEach(movie => {
              this.movies.push(movie)
            })

            console.log(this.movies)
          }
          )

      }).catch(error => console.log(error)
      );
  }
}
</script>

<style>
</style>
