<template>

  <div class="FrenchMovies">

    <h2>French Movies</h2>

<SortButtons :movies="movies" ></SortButtons>

     <MovieList :movies="movies" :loading="loading" :errored="errored"></MovieList>

  </div>

</template>

<script>

import MovieList from "./utils/MovieList.vue";
import SortButtons from "./utils/SortButtons.vue";
import axios from "axios";



export default {
  name: "FrenchMovies",
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
    axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=1&vote_count.gte=1000&with_original_language=fr")
      .then((firstAPIresponse) => {
        this.movies = firstAPIresponse.data.results;
        console.log(this.movies)

        axios.get("https://api.themoviedb.org/3/discover/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en&sort_by=popularity.desc&include_adult=false&include_video=true&page=2&vote_count.gte=1000&with_original_language=fr")
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