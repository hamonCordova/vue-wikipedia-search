<template>

    <header>
        <div class="fluid-container header-bg">
            <div class="container header-content">
                <div class="row">
                    <div class="col-sm-12">
                        <h1>Wikipedia Search</h1>
                        <h2>Seach for anything in Wikipedia API</h2>
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

    .header-bg {
     background-image: url('https://images.unsplash.com/photo-1427504494785-3a9ca7044f45?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80');
      //  background-image: url('https://images.unsplash.com/photo-1533669955142-6a73332af4db?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=839&q=80');
    //    background-image: url('https://images.unsplash.com/photo-1505664063603-28e48ca204eb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80');
        background-size: cover;  
        background-position: 0px -180px;
        height: 200px;
        padding: 20px 0px;
    }

    .header-content {
        margin-top: 50px;
    }

    header {
        text-align: center;
    }

    h1 {
        color: #fff;    
        font-size: 2.8rem;
        text-shadow: 2px 2px 3px rgba(0,0,0,0.4);
    }

    h2 {
        color: #ccc;
        font-weight: normal;
        font-size: 1.2rem;
    }

</style>