<template>
    <div class="container-fluid">
      <VueSlickCarousel v-bind="settings">
        <Card v-for="card in cards" :key="card.id" :card="card"/>
      </VueSlickCarousel>
    </div>
  </template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import Card from '~/components/Card.vue'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  components: { 
    VueSlickCarousel,
    Card
   },
  data(){
    return {
        cards: [],
        settings: {
            "dots": true,
            "focusOnSelect": true,
            "infinite": true,
            "speed": 500,
            "slidesToShow": 3,
            "slidesToScroll": 1,
            "touchThreshold": 5,
            "autoplay": true,
            "autoplaySpeed": 3000,
        }
    }
  },
  async fetch(){
      this.cards = await this.$strapi.find('cards')
  }
}
</script>

<style scoped>
.container-fluid{
    width: 1110px;
}
</style>