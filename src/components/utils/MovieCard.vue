
<template>

  <router-link :to="`/MovieDetails/${id}`">


    <div class="card text-bg-ligth mb-3" style="max-width: 20rem;">
      <div class="card-header"> <img v-bind:src="preUrl + poster_path" alt="moviePoster" /></div>
      <div class="card-body">
        <h5 class="card-title"> {{ title }}</h5>
        <p><b> Score :</b> {{ vote_average }} </p>
        <p><b> Release :</b> {{ release_date }} </p>
        <p><b> Sinopse:</b> {{ overview.substring(0, 160) + "... Read more ... " }}</p>
      </div>
    </div>

  </router-link>

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

<style scoped>
a {
  text-decoration: none;
  color: white;
}

.card {
  height: 90vh;
}


</style>