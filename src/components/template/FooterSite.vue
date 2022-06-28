<template>

    <div class="footer container-fluid">
        <div class="card-header">
            I am a footer <footer>
                <div class="card-body">
                    <blockquote class="blockquote mb-0">
                        <p>I am a copy rigth text</p>
                        <footer class="blockquote-footer">Happy Movies <cite title="Source Title">2022</cite></footer>
                    </blockquote>
                </div>
            </footer>
        </div>

    </div>

</template>

<script>
export default {
    name: "FooterApp",
}
</script>

<style>
.footer {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    height: 24vh;
    color: white;
    background-color: black;
    font-family: 'Stick No Bills', sans-serif;
}
</style>