<template>

    <div class="footer container-fluid">
        <div class="card-header">
            Your favorite movies make us Happy! <footer>
                <div class="card-body">
                    <blockquote class="blockquote mb-0">
                        <h3>© All the rights reserved</h3>
                        <h3>Happy Movies 2022</h3>
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

@media screen and (max-width: 768px) {
  h2 {
    font-size: 2rem;
    text-align: center;

  }

}
</style>