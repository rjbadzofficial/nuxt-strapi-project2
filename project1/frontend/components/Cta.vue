<template>
    <div :style="{background: `linear-gradient(0deg, rgba(0,118,163,.75) 0%, rgba(0,118,163,.75) 100%), url(${getMedia(imageUrl)}) no-repeat`}">
        <h2>{{description}}</h2>
        <nuxt-link to="/contactus">Contact Us</nuxt-link>
    </div>
</template>

<script>
import { getMedia } from '~/utils/media'
export default{
    props: ['slug'],
    data(){
        return{
            imageUrl: '',
            description: ''
        }
    },
    methods: {
        getMedia
    },
    async fetch(){
        await this.$strapi.find('ctas', { slug: this.slug })
        .then(cta => {
            this.imageUrl = cta[0].image.url
            this.description = cta[0].description
        })
    }
}
</script>

<style scoped>
h2{
    color: #ffffff;
    max-width: 60rem;
    margin: 0;
    text-align: center;
    padding: 1rem;
}
div{
    padding: 12rem 0;
    background-size: cover !important;
    background-position: center !important;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
a{
    text-decoration: none;
    color: #ffffff;
    background-color: #ffa400;
    padding: 1rem 2rem;
    position: relative;
    top: 2rem;
}
a:hover{
    background-color: #00b6e6;
}
</style>