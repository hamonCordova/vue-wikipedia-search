<template>

    <header>
        <div class="container">
            <div class="row">
                <div class="col-sm-12">
                    <h1>Wikipedia Search</h1>
                    <h2>Seach for anything in Wikipedia API</h2>
                </div>
            </div>
        </div>
    </header>

</template>

<script>
export default {
    name: 'Header'
}
</script>

<style lang="scss" scoped>

    header {
        margin-top: 5%;
        text-align: center;
    }

    h1 {
        color: rgb(37, 37, 37);
        font-size: 2.8rem;
        text-shadow: 2px 2px 3px rgba(0,0,0,0.3);
    }

    h2 {
        color: rgb(235, 235, 235);
        font-weight: normal;
        font-size: 1.2rem;
    }

</style>