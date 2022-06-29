<template>

        <h1>Happy Movies</h1>

    <nav class="navbar navbar-expand-lg bg-light">

        <div class="container-fluid">

            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup"
                aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarNavAltMarkup">

                <div class="navbar-nav">

                    <router-link class="nav-link active" to="/">Home</router-link>
                    <router-link class="nav-link" to="/AmericanMovies">American Movies</router-link>
                    <router-link class="nav-link" to="/FrenchMovies">French Movies</router-link>
                    <router-link class="nav-link" to="/LastMovies">Last Movies</router-link>
                    <router-link class="nav-link" to="/SearchMovies">Search Movies</router-link>
                    <router-link class="nav-link" to="/TopRatedMovies">Top Rated Movies</router-link>

                </div>

            </div>

        </div>

    </nav>

</template>

<script>

export default {
    name: "HeaderNav",
}

</script>

<style scoped>
h1 {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 6rem;
    height: 24vh;
    color: white;
    background-color: black;
    font-family: 'Rubik Moonrocks', cursive;
}

nav{
    padding-left: 15%;
}

a{
    font-size: 20px;
      font-family: 'Gloria Hallelujah', cursive;
      margin: 12px;
      color: black;
}
</style>