<template>
    <img :width="`${width}px`" :src="`http://localhost:1337${logo[0].image.url}`" :alt="logo[0].image.title">
</template>

<script>
export default {
    props: {
        width: 0,
        height: 0
    },
    data(){
        return {
            logo: []
        }
    },
    async fetch(){
        this.logo = await this.$strapi.find('logos')
    }
}
</script>