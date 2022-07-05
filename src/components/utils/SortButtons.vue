<template>
    <div class="sortbuttons">

        <button id="Alphabetical" @click="sortByTitle" type="button" class="btn btn-outline-secondary"> For Order
            Alphabetical</button>
        <button id="Release" @click="sortByDate" type="button" class="btn btn-outline-secondary">For Release
            Date</button>
        <button id="Score" @click="sortByRating" type="button" class="btn btn-outline-secondary">For Score</button>

    </div>
</template>

<script>

export default {
    name: "SortButtons",
    props: ["movies"],
    emits: ['sortByRating', 'sortByDate', 'sortByTitle'],

    data() {
        return {
            inversenote: false,
            inversetitle: false,
            inversedate: false,
        }
    },

    methods: {

        sortByRating() {
            let movielist = this.movies

            if (this.inversenote == true) {

                movielist.sort(function sortarray(movie1, movie2) {
                    if (movie1.vote_average > movie2.vote_average) {
                        return -1;
                    }
                    if (movie1.vote_average < movie2.vote_average) {
                        return 1;
                    }
                    return 0;
                })

                return this.inversenote = false
            }
            if (this.inversenote == false) {

                movielist.sort(function sortarray(movie1, movie2) {
                    if (movie1.vote_average < movie2.vote_average) {
                        return -1;
                    }
                    if (movie1.vote_average > movie2.vote_average) {
                        return 1;
                    }
                    return 0;
                })
                return this.inversenote = true

            }
        },

        sortByDate() {
            let movielist = this.movies

            if (this.inversedate == true) {

                movielist.sort((movie1, movie2) => {
                    if (movie1.release_date < movie2.release_date) {
                        return -1;
                    }
                    if (movie1.release_date > movie2.release_date) {
                        return 1;
                    }
                    return 0;
                })

                return this.inversedate = false
            }

            if (this.inversedate == false) {

                movielist.sort((movie1, movie2) => {
                    if (movie1.release_date > movie2.release_date) {
                        return -1;
                    }
                    if (movie1.release_date < movie2.release_date) {
                        return 1;
                    }
                    return 0;
                })
                return this.inversedate = true
            }
        },

        sortByTitle() {
            let movielist = this.movies

            if (this.inversetitle == true) {

                movielist.sort((movie1, movie2) => {
                    if (movie1.title < movie2.title) {
                        return -1;
                    }
                    if (movie1.title > movie2.title) {
                        return 1;
                    }
                    return 0;
                })

                return this.inversetitle = false
            }

            if (this.inversetitle == false) {

                movielist.sort((movie1, movie2) => {
                    if (movie1.title > movie2.title) {
                        return -1;
                    }
                    if (movie1.title < movie2.title) {
                        return 1;
                    }
                    return 0;
                })
                return this.inversetitle = true
            }
        },

    }
}


</script>

<style scoped>
.sortbuttons {
    display: flex;
    justify-content: center;
    justify-content: space-around;
    padding: 3rem;
}

.btn {
    font-family: 'Fredoka One', cursive;
    background-color: black;
    color: #fff;
    font-size: 1.5rem;
    height: 6rem;
    width: 16rem;
    border-radius: 25px;
}

@media screen and (max-width: 768px) {
    .sortbuttons {
        flex-direction: column;
        align-items: center;
        margin-top: 20px;
        gap: 20px;
    }

}
</style>