
<template>

    <div>

        <ul>

            <li class= "list-unstyled" v-for="movie in movies" v-bind:key="movie.id">
                <MovieCard :id="movie.id" :title="movie.title" :poster_path="movie.poster_path"
                    :release_date="movie.release_date" :vote_average="movie.vote_average" :overview="movie.overview" />
            </li>

        </ul>

    </div>

</template>

<script>

import MovieCard from './MovieCard.vue'

export default {
    name: "MovieList",
    components: {
        MovieCard
    },

    props: ["movies"]
}


</script>

<style scoped>

ul{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding-left: 0;
    margin: 5%;
}

</style>