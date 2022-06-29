
<template>

    <div v-if="!loading" class="container-fluid ">

        <h5> {{ movie.title }} </h5>

        <div class="row">

            <div class="col-4 col-sm-3" > <img v-bind:src="preUrl + movie.poster_path" alt="moviePoster" /></div>
            <div class="col-8 mt-4 col-sm-3">
                <p><b> Score :</b> {{ movie.vote_average }} </p>
                <p><b> Total Votes :</b> {{ movie.vote_count }} </p>
                <p><b> Release :</b> {{ movie.release_date }} </p>
                <p><b> Trailer :</b> {{ movie.video }} </p>
                <p><b> Sinopse:</b> {{ movie.overview }}</p>
            </div>

        </div>

    </div>

</template>

<script>

import axios from "axios"

export default {
    name: "MovieDetails",
    data() {
        return {
            movie: null,
            preUrl: "https://image.tmdb.org/t/p/original/",
            idMovie: this.$route.params.id,
            loading: true
        };
    },

    created() {
        // appel api
        axios.get("https://api.themoviedb.org/3/movie/" + this.idMovie + "?api_key=3ea8988340d4ed715d28b9978346c29e&language=en-US")
            .then((res) => {
                this.movie = res.data
                this.loading = false
                console.log(this.movie)
            }
            )
    }
}

</script>

<style scoped>
.row{
    display: flex;
    justify-content: center;
    justify-content: space-around;
    margin-bottom: 5%;
}

img{
height: 90vh;
}

b{
    font-size: 2rem;
}

p{
    font-size: 1.5rem;
}

h5{
    font-size: 3rem;
    margin: auto;
}
</style>


