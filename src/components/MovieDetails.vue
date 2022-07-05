
<template>

    <div v-if="!loading" class="container-fluid ">

        <h5 class="text-center"> {{ movie.title }} </h5>

        <p class="fst-italic fs-2 text text-center" v-if="movie.tagline != ''"> {{ movie.tagline }}</p>

        <div class="row">

            <div class="col-6 col-lg-6 col-sm-6 text-center " > <img v-bind:src="preUrl + movie.poster_path" alt="moviePoster" /></div>
            <div class="col-6 col-lg-6 mt-4 col-sm-6 text-center ">

                <div class="mt-5" id="trailer" v-if="video[0]">
                    <iframe width="650" height="300" v-bind:src="'https://www.youtube.com/embed/' + video[0].key"
                        frameborder="0"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                        allowfullscreen class="shadow"></iframe>
                </div>

                <div class="texto">

                    <p><b> Score :</b> {{ movie.vote_average }} </p>
                    <p><b> Total Votes :</b> {{ movie.vote_count }} </p>
                    <p><b> Release :</b> {{ movie.release_date }} </p>
                    <p v-if="movie.budget != '0'"><b> Budget :</b> {{ movie.budget }} </p>
                    <p><b> Language :</b> {{ movie.original_language }} </p>
                    <p><b> Gender: </b><span v-for="genresall in movie.genres" v-bind:key="genresall.id"> / {{genresall.name}} &nbsp;</span></p>
                    <p><b> Sinopse:</b> {{ movie.overview }}</p>

                </div>




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
            video: null,
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

        axios.get("https://api.themoviedb.org/3/movie/" + this.idMovie + "/videos?api_key=3ea8988340d4ed715d28b9978346c29e&language=US")
            .then((response) => {
                this.video = response.data.results;
                console.log(this.video);
            });
    },
}

</script>

<style scoped>
.row{
display: flex;
justify-content: center;
align-items: center;
}

img {
    height: 90vh;
}

h5 {
    font-size: 3rem;
    margin: auto;
}
.texto{
width:40%;
margin-top: 5%;
}
</style>


