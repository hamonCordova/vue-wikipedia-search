<template>
    <div class="fluid-container footer">
        <span>Wikipedia Search</span> <br>
        <span class="author">Created By Hamon Córdova</span>
    </div>
</template>

<script>

export default {
    name: 'Footer',
    props: []
}

</script>



<style lang="scss" scoped>

    .footer {
        width: 100%;
        background: #666;
        height: auto;
        padding: 10px;
        font-size: 1.3rem;
        text-align: center;
        color: #f1f1f1;
        position: absolute;
        bottom: 0;

        .author {
            font-size: 1rem;
        }

    }

</style>