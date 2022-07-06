<template>
    <div class="container">
        <router-link :to="`/MovieDetails/${id}`">
            <div class ="card p-1 my-3 ">
                <h5 class ="title fs-4 text-center text-white text-uppercase">{{ title }}</h5>
                <img v-bind:src="preUrl + poster_path" alt="moviePoster" />
                <div class="card-body">
                    <p class="sorti text-white fs-5 text"><b>Sortie :</b> {{ release_date }}</p>
                    <p class="notemoy text-white fs-5 text"><b>Note moyenne :</b> {{ vote_average }}</p>
                    <p class="resum text-white fs-5 text"><b>Résumé :</b> {{ overview.substring(0, 200) + "..." }}</p>
                </div>
            </div>
        </router-link>
    </div>
</template>

<script>

export default {
  name: "MovieCard",
  props: ["id", "title", "vote_average", "release_date", "overview", "poster_path"],

  data() {
    return {
      preUrl: "https://image.tmdb.org/t/p/original/",
    };
  },
}

</script>

<style>

 a{
    text-decoration: none;
}

img{
    height: 60vh;
}

.card {
    border: 1px solid #000;
    background-color: #000;
    text-align: left;
    width: 30rem;
    height: 100vh;
}

@media screen and (max-width: 768px) {
 
 .card {
    width: 20rem;
}

}

</style>