<template>
    <div class="container-fluid">
        <div class="banner row" :style="{background: `linear-gradient(87deg, rgba(0,118,163,0.8757878151260504) 0%, rgba(255,255,255,.15) 90%), url(${getMedia(imageUrl)})`}">
            <div class="col-md-8">
                <h1>{{title}}</h1>
                <hr>
                <p>{{description}}</p>
                <p>{{description2}}</p>
                <blockquote><span class='open quote'>" </span>{{tagline}}<span class='close quote'> "</span></blockquote>
                <nuxt-link class="learnmore" to="/contactus">Learn More</nuxt-link>
            </div>
        </div>
    </div>
</template>

<script>
import { getMedia } from '~/utils/media';
export default{
    data(){
        return {
            imageUrl: '',
            title: '',
            description: '',
            description2: '',
            tagline: '',
        }
    },
    methods: {
        getMedia
    },
    async fetch(){
        await this.$strapi.find('banners', {slug: 'home'}).then(banner => {
            this.imageUrl = banner[0].image.url
            this.title = banner[0].title
            this.description = banner[0].description
            this.description2 = banner[0].description2
            this.tagline = banner[0].tagline
        })
    }
}
</script>

<style scoped>
.banner{
    color: #ffffff;
    border-radius: 10px;
    background-repeat: no-repeat !important;
    background-position: top right !important;
    background-size:  cover !important;
    padding: 6rem 2.5rem;
    border-bottom: 0.75rem solid #00b6e6;
    max-width: 1110px;
    width: 100%;
    margin: 0 auto;
}
.banner h1{
    font-weight: bold;
    font-size: clamp(2rem, 0.4rem + 5.3333vw, 3.5rem);
}
.banner p{
    font-size: 1.25rem;
}
hr{
    min-width: 5rem;
    max-width: 16rem;
    width: 100%;
    height: 0.5rem;
    background-color: #00b6e6;
    opacity: 1;
    border: none;
    margin-top: 2rem;
    margin-bottom: 1.75rem;
}
blockquote{
    font-size: clamp(1.5rem, 0.4rem + 5vw, 2rem);
    font-style: italic;
    margin: 3rem 0;
}
blockquote span{
    font-family: Calibri;
    color: #ffffff;
    font-size: 34px;
}
.learnmore{
    text-decoration: none;
    color: #ffffff;
    background-color: #ffa400;
    text-transform: uppercase;
    font-weight: bold;
    border-radius: 6px;
    padding: 1rem;
    display: inline-block;
    max-width: 400px;
    width: 100%;
    text-align: center;
}

</style>