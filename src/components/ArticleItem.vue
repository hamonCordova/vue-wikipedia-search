<template>
    <div>
        <div class="row">
            <div class="col-sm-3">
                <img v-if="canShowImage(article)" :src="[article.original.source]" />
                <img v-else src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ-BelEglBTNwGO8pFEmfe8tvespnuM-dxNUbTFZ-Ac2GU5rzH6Xw&s" />
            </div>
            <div class="col-sm-8">
                <h2>{{ article.title }}</h2>
                <p>{{ article.extract }}</p>
                <a class="btn btn-danger pull-right" target="_blank" :href="['https://en.wikipedia.org/?curid=' + article.pageid]">Read More</a>
            </div>
        </div>

    </div>

</template>

<script>
export default {
    name: 'ArticleItem',
    props: ['article'],
    methods: {
        canShowImage(article) {

            if(!article.original) {
                return false;
            }

            let sourceExtension = article.original.source.substr(-4).toLowerCase();
            let acceptedExtension = ['.jpg', '.png', 'jpeg', '.gif'];

            if(acceptedExtension.includes(sourceExtension)) {
                return true;
            }

        }
    }
}
</script>

<style lang="scss" scoped>

    .row {
        padding: 25px 0px;
        border-bottom: 1px solid #ccc;
        box-shadow: 1px 1px 2px 1px rgba(0, 0, 0, 0.1);
        background: #fff;
        margin: 10px 0px;
    }

    img {
        width: 100%;
        min-width: 100%;
        border: 1px solid #f1f1f1;
    }

    h2 {
        margin-top: 10px;
        @media screen and (min-width: 768px) {
            margin-top: 0px;
        }
    }

    a {
        float: right;
        width: 100%;
        @media screen and (min-width: 768px) {
            width: auto;
        }
    }


</style>