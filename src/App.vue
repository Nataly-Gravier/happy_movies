<template>

  <div id="app">

    <HeaderNav />

    <div v-if="$route.path == '/'">
      <!-- if the route is this one  / -->

      <h2 class="pt-5 font-weight-light"> Your favorite movies make us Happy! </h2>

      <div class="movieshome">
        <MovieList :movies="movies" :loading="loading" :errored="errored" />
      </div>

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
      movies: null,
      loading: true,
      errored: false,
    }
  },

  created() {
    axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=1&vote_count.gte=1200&with_watch_monetization_types=flatrate")
      .then((firstAPIresponse) => {
        this.movies = firstAPIresponse.data.results;
        console.log(this.movies)

        axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=2&vote_count.gte=1200&with_original_language=en&with_watch_monetization_types=flatrate")
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

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Fredoka One', cursive;
}

h2 {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 4rem;
  height: 14rem;
  color: white;
  background-color: black;
}

@media screen and (max-width: 768px) {
  
  h2 {
    font-size: 2.3rem;
    text-align: center;

  }

}

@media screen and (max-width: 1024px) {
body{
  margin-top: 5%;
}

  h2 {
    font-size: 3;
    text-align: center;

  }

}
</style>
