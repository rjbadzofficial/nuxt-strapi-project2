<template>
    <div class="banner" :style="`background: linear-gradient(87deg, rgba(0,118,163,.5) 25%, rgba(247, 204, 105,.5) 100%), url(${getMedia(imageUrl)})`">
        <div class="container-fluid">
            <h3>Products</h3>
            <h1>{{title}}</h1>
            <p>{{description}}</p>
        </div>
    </div>
</template>

<script>
import { getMedia } from '~/utils/media'
export default {
    props: ['slug'],
    data() {
        return {
            imageUrl: '',
            title: '',
            description: ''
        }
    },
    methods: {
        getMedia
    },
    async fetch(){
        await this.$strapi.find('banners', { slug: this.slug }).then(banner => {
            this.imageUrl = banner[0].image.url
            this.title = banner[0].title
            this.description = banner[0].description
        })
    }
}
</script>

<style scoped>
.banner{
    padding: 7rem 0 5rem 0;
    background-position: center right !important;
    background-size: cover !important;
    color: #ffffff;
}
.banner .container-fluid{
    width: 1110px;
}
.banner h1{
    font-weight: bold;
    font-size: 2.75rem;
    margin-bottom: 2.5rem;
}
.banner h3{
    font-size: 1rem;
    margin-bottom: 0;
}
.banner p{
    width: 45%;
}

</style>