
<template>

    <div class="searchmovies">

        <h2>Search For Your Movies</h2>

        <div class="container-fluid">
            <p>Use me to find your move</p>
            <input v-model="search" @keyup="getSearch(search)" />
        </div>

    </div>

    <MovieList :movies="movies" :loading="loading" :errored="errored" />

</template>

<script>

import MovieList from "./utils/MovieList.vue";

import axios from "axios";

export default {

    name: "SearchMovies",
    components: {
        MovieList,
    },

    data() {

        return {
            movies: null,
            loading: true,
            errored: false,
        };

    },

    methods: {
        sortMovies(movies) {
            this.movies = movies
        },

        getSearch(search) {
            axios.get("https://api.themoviedb.org/3/search/movie?api_key=3ea8988340d4ed715d28b9978346c29e&language=en-US&include_adult=false&query=" + search)
                .then((responsefive) => {
                    this.movies = responsefive.data.results;
                });
        },
    },
};
</script>

<style scoped>

.container-fluid{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

input{
    height: 3rem;
    width: 20rem;
    border-radius: 20px;
}

p{ text-align: center;
  font-size: 2rem;
}

.searchmovies{
    margin-top: 10%;
    margin-bottom: 10%;

}
</style>