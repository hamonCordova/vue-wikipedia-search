<template>

    <header>
        <div class="fluid-container header-bg">
            <div class="container header-content">
                <div class="row">
                    <div class="col-sm-12">
                        <h1>Wikipedia Search</h1>
                        <h2>Search for anything on Wikipedia API</h2>
                    </div>
                </div>
            </div>
        </div>
    </header>

</template>

<script>

import axios from "axios";

export default {
    name: 'Header',
    data() {
        return {
        }
    },
    created() {
    },
    methods: {
        
    }
}
</script>

<style lang="scss" scoped>

    $headerHeight: 350px;

    .header-bg {
        background-image: url('https://images.wallpaperscraft.com/image/books_library_collection_125386_2560x1080.jpg');
        background-size: cover;  
        height: $headerHeight;
        filter: grayscale(0%);
        padding: 0.1px 0px;

        @media screen and (min-width: 768px) {
            $headerHeight: 250px;
            height: $headerHeight;
        }

    }

    .header-content {
        margin-top: calc((#{$headerHeight} / 4) - 10px);
        text-shadow: 2px 2px 3px rgba(0,0,0,0.4);
        padding: 5px;
    }

    header {
        text-align: center;
    }

    h1 {
        color: #fff;    
        font-size: 4.2rem;

        @media screen and (min-width: 768px) {
            font-size: 4.8rem;
        }

    }

    h2 {
        color: #fff;
        font-weight: normal;
        font-size: 1.2rem;
        position: relative;
       

        @media screen and (min-width: 768px) {
            top: -18px;
            left: 35px;
        }

    }

</style>