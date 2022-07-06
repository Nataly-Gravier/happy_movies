<template>

    <h1 class="container-fluid">Happy Movies</h1>


    <nav class="navbar navbar-expand-lg bg-white">

        <div class="container-fluid">

            <div class="mx-auto">

                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                    aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>

                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav">
                        <router-link class="nav-link active" to="/">Home</router-link>

                        <li class="nav-item">
                            <router-link class="nav-link" to="/AmericanMovies">American Movies</router-link>
                        </li>
                        <li class="nav-item">
                            <router-link class="nav-link" to="/FrenchMovies">French Movies</router-link>
                        </li>
                        <li class="nav-item">
                            <router-link class="nav-link" to="/LastMovies">Last Movies</router-link>
                        </li>
                        <li class="nav-item">
                            <router-link class="nav-link" to="/TopRatedMovies">Top Rated Movies</router-link>
                        </li>
                        <li class="nav-item">
                            <router-link class="nav-link" to="/SearchMovies">Search Movies</router-link>
                        </li>
                    </ul>
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
    background-image: url(@/assets/movies.jpg);
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 7rem;
    height: 14rem;
    color: black;
}

a {
    font-size: 2rem;
    text-decoration: none;
    margin: 40px;
    color: black;
}

nav {
    display: flex;
    justify-content: center;
    align-items: center;
}

@media screen and (max-width: 768px) {
    h1 {
        font-size: 5rem;
    }

}

@media screen and (max-width: 1024px) {

    nav {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        z-index: 1;
    }

}
</style>