<template>
    <div class="card">
        <div :class="right ? 'title_description left' : 'title_description right'">
            <h2>{{title}}</h2>
            <p>{{description}}</p>
        </div>
        <div class="image" :style="`background: url(${getMedia(imageUrl)})`"></div>
        <nuxt-link :to="link" :class="right ? 'link left' : 'link right'">Go to Product List</nuxt-link>
    </div>
</template>

<script>
import { getMedia } from '~/utils/media';
export default {
    props: {
        title: String,
        description: String,
        imageUrl: String,
        link: String,
        right: Boolean
    },
    methods: {
        getMedia
    }
}
</script>

<style scoped>
.card{
    width: 100%;
    max-width: 480px;
}
.title_description h2{
    color: #ffffff;
}

.title_description.left{
    position: relative;
    padding: 2rem 1rem 4rem 1rem;
    background-color: #ffa400;
    color: #ffffff;
    height: 250px;
}
.title_description.left::after{
    position: absolute;
    content: '';
    bottom: 0;
    left: 2rem;
    border-left: 35px solid transparent;
    border-right: 35px solid transparent;
    border-top: 35px solid #ffa400;
    transform: translateY(100%);
}
.image{
    height: 400px;
    background-position: center right !important;
    background-size: cover !important;
    background-repeat: no-repeat;
}
.link.left{
    background-color: #ffa400;
    text-align: center;
    color: #ffffff;
    text-decoration: none;
    cursor: pointer;
    padding: 1rem;
    transition: all 0.4s;
}
.link.left:hover{
    background-color: #ec9905;
    transform: scale(1.01);
}
.title_description.right{
    position: relative;
    padding: 2rem 1rem 4rem 1rem;
    background-color: #0076a3;
    color: #ffffff;
    height: 250px;
}
.title_description.right::after{
    position: absolute;
    content: '';
    bottom: 0;
    right: 2rem;
    border-left: 35px solid transparent;
    border-right: 35px solid transparent;
    border-top: 35px solid #0076a3;
    transform: translateY(100%);
}
.link.right{
    background-color: #0076a3;
    text-align: center;
    color: #ffffff;
    text-decoration: none;
    cursor: pointer;
    padding: 1rem;
    transition: all 0.4s;
}
.link.right:hover{
    background-color: #066386;
    transform: scale(1.01);
}
</style>