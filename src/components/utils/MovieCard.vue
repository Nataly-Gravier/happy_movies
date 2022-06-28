
<template>

    <div class="card" style="width: 18rem;">

        <h5 class="card-title"> {{ title }} </h5>

        <img v-bind:src="preUrl + poster_path" alt="moviePoster" />

        <div class="card-body">

            <p><b> Score :</b> {{ vote_average }} </p>
            <p><b> Release :</b> {{ release_date }} </p>  
            <p ><b> Sinopse:</b> {{ overview.substring(0,160) + "... Read more ... "  }}</p>

        </div>

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

card{
  height: 60vh;
}

</style>