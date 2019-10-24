<template>
    <div>
        <h2>{{ article.title }}</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Nulla in voluptatum nobis expedita nemo nam voluptatem, id tempora dolore, aperiam ipsam beatae perspiciatis officia illo voluptatibus voluptas ea iure dignissimos vel quia rerum sint non? At, illum facilis? Autem cupiditate cum perferendis rerum impedit et corrupti ullam accusamus aliquid adipisci quo quis quos tempora incidunt omnis, consectetur quidem animi pariatur? Quia aperiam suscipit, ducimus laboriosam iste dolor ea libero id odit. Odit dignissimos mollitia, quo, omnis dicta explicabo laborum itaque praesentium modi maxime rerum ad quidem ipsa rem quisquam esse possimus ducimus. Architecto neque pariatur quas id nulla, ut nostrum.</p>
        <button class="btn btn-primary">Read More</button>
        <hr>
    </div>
</template>

<script>
export default {
    name: 'ArticleItem',
    props: ['article'],
}
</script>