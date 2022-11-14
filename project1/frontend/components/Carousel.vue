<template>
    <div class="container-fluid">
      <VueSlickCarousel v-bind="settings" :slidesToShow="display">
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
        display: 3,
        settings: {
            "dots": true,
            "focusOnSelect": true,
            "infinite": true,
            "speed": 500,
            "slidesToShow": this.display,
            "slidesToScroll": 1,
            "touchThreshold": 5,
            "autoplay": true,
            "autoplaySpeed": 3000,
        }
    }
  },
  async fetch(){
      this.cards = await this.$strapi.find('cards')
  },
  mounted() {
    window.addEventListener("load", this.onResize);
    window.addEventListener("resize", this.onResize);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      if(window.innerWidth < 443 + 15){
        this.display = 1
      }else if(window.innerWidth < 768 + 15){
        this.display = 2
      }else{
        this.display = 3
      }
    }
  }
}
</script>

<style scoped>
.container-fluid{
    max-width: 1100px;
    width: 100%;
}
</style>