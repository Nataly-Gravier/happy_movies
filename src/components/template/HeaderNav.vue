<template>

            <router-link to="/"> <h1>Happy Movies</h1> </router-link>

    <nav class="navbar navbar-expand-lg bg-light ">

        <div class="container-fluid ">

            <router-link to="/"> Accueil</router-link>

            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="true"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse d-flex justify-contente-around " id="navbarSupportedContent">

                <ul class="navbar-nav me-auto mb-2 mb-lg-0">

                    <li class="nav-item">
                        <router-link to="/AmericanMovies">American Movies</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/FrenchMovies">French Movies</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/LastMovies">Last Movies</router-link>
                    </li>

                    <li class="nav-item">
                        <router-link to="/SearchMovies">Search Movies</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/TopRatedMovies">Top Rated Movies</router-link>
                    </li>

                </ul>

                <form class="d-flex" role="search">

                    <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">

                    <button class="btn btn-outline-dark" type="submit">Search</button>

                </form>

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

nav {
    display: flex;
    justify-content: center;
    justify-content: space-around;
    font-family: 'Stick No Bills', sans-serif;
}
</style>