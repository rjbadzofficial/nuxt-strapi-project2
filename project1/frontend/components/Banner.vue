<template>
    <div class="container-fluid">
        <div class="banner row" :style="{backgroundImage: `url(http://localhost:1337${banners[0].image.url})`}">
            <div class="col-md-6">
                <h1>{{banners[0].title}}</h1>
                <hr>
                <p>{{banners[0].description}}</p>
                <p>{{banners[0].description2}}</p>
                <blockquote>{{banners[0].tagline}}</blockquote>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return {
            banners: []
        }
    },
    async fetch(){
        this.banners = await this.$strapi.find('banners')
    }
}
</script>

<style scoped>
.banner{
    color: #ffffff;
    border-radius: 10px;
}
.banner h1{
    font-weight: bold;
    font-size: 3rem;
}
hr{
    width: 16rem;
    height: 0.5rem;
    background-color: #00b6e6;
    opacity: 1;
    border: none;
}
@media (min-width: 992px) {
    .container-fluid{
        width: 1060px;
    }
}
</style>