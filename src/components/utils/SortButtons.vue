<template>
    <div>

        <button type="button" class="btn btn-outline-secondary"> For Order Alphabetical</button>
        <button type="button" class="btn btn-outline-secondary">For Release Date</button>
        <button type="button" class="btn btn-outline-secondary">For Score</button>

    </div>
</template>

<script>
export default {
    name: "SortButtons",
    data() {
        return {
            movies: null,
        };
    },
}
</script>

<style scoped>

.btn {
    font-family: 'Gloria Hallelujah', cursive;
    background-color:black;
    color: #fff;
    font-size: 1.5rem;
    margin: 2% 10% 2% 12%;
    height: 5rem;
    width: 12rem;
}
</style>