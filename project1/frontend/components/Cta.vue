<template>
    <div :style="{background: `linear-gradient(0deg, rgba(0,118,163,.75) 0%, rgba(0,118,163,.75) 100%), url(http://localhost:1337${ctas[0].image.url}) no-repeat`}">
        <h2>{{ctas[0].description}}</h2>
        <nuxt-link to="">Contact Us</nuxt-link>
    </div>
</template>

<script>
export default{
    data(){
        return{
            path: this.$route.path,
            ctas: []
        }
    },
    async fetch(){
        this.ctas = await this.$strapi.find('ctas', { path: this.path})
    }
}
</script>

<style scoped>
h2{
    color: #ffffff;
    max-width: 60rem;
    margin: 0;
    text-align: center;
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