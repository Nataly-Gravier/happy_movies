<template>
    <div>

        <button type="button" class="btn btn-outline-secondary">Secondary</button>
        <button type="button" class="btn btn-outline-secondary">Secondary</button>
        <button type="button" class="btn btn-outline-secondary">Secondary</button>

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
    background-color:black;
    color: #fff;
    margin: auto 10% auto 15%;
}
</style>