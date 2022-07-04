<template>

  <div class="TopRatedMovies">

    <h2>Top Rated Movies </h2>

    <SortButtons :movies="movies"></SortButtons>

    <MovieList :movies="movies" :loading="loading" :errored="errored" />

  </div>

</template>

<script>

import MovieList from "./utils/MovieList.vue";
import SortButtons from "./utils/SortButtons.vue";
import axios from "axios";

export default {
  name: "TopRatedMovies",
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
    axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=1&vote_count.gte=1000&vote_average.gte=8")
      .then((firstAPIresponse) => {
        this.movies = firstAPIresponse.data.results;
        console.log(this.movies)

        axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=2&vote_count.gte=1000&vote_average.gte=8")
          .then((secondAPIresponse) => {

            secondAPIresponse.data.results.forEach(movie => {
              this.movies.push(movie)
            })

            console.log(this.movies)
          }
          )

        axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=3&vote_count.gte=1000&vote_average.gte=8")
          .then((thirdAPIresponse) => {

            thirdAPIresponse.data.results.forEach(movie => {
              this.movies.push(movie)
            })
            this.movies.splice(10, 10)

            console.log(this.movies)
          }
          )

      }).catch(error => console.log(error)
      );
  }
}

</script>