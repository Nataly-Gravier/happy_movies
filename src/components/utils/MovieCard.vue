
<template>

    <div class="card" style="width: 18rem;">

        <h5 class="card-title"> {{ title }} </h5>

        <img v-bind:src="preUrl + poster_path" alt="moviePoster" />

        <div class="card-body">

            <p>{{ vote_average }}</p>
            <p>{{ release_date }}</p>
            <p>{{ overview }}</p>

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