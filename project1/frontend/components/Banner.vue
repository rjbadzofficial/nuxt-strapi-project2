<template>
    <div class="container-fluid">
        <div class="banner row" :style="{background: `linear-gradient(87deg, rgba(0,118,163,0.8757878151260504) 0%, rgba(255,255,255,.15) 90%), url(http://localhost:1337${banners[0].image.url})`}">
            <div class="col-md-8">
                <h1>{{banners[0].title}}</h1>
                <hr>
                <p>{{banners[0].description}}</p>
                <p>{{banners[0].description2}}</p>
                <blockquote><span class='open quote'>" </span>{{banners[0].tagline}}<span class='close quote'> "</span></blockquote>
                <nuxt-link class="learnmore" to="/">Learn More</nuxt-link>
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
    background-repeat: no-repeat !important;
    background-position: top !important;
    background-size: cover !important;
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