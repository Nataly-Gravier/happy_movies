<template>

  <div class="LastMovies">

    <h1>Last Movies </h1>

    <SortButtons :movies="movies" @sort-movies="sortMovies"></SortButtons>

    <MovieList :movies="movies" :loading="loading" :errored="errored" />

  </div>

</template>

<script>

import MovieList from "./utils/MovieList.vue";
import SortButtons from "./utils/SortButtons.vue";
import axios from "axios";



export default {
  name: "LastMovies",
  components: {
    MovieList,
    SortButtons
  },
  data() {
    return {
      movies: null,
      loading: true,
      errored: false,
    };
  },

  created() {
    axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en-US&region=France&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&year=2022")
      .then((firstAPIresponse) => {
        this.movies = firstAPIresponse.data.results;
        console.log(this.movies)

        axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en-US&region=France&sort_by=popularity.desc&include_adult=false&include_video=false&page=2")
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