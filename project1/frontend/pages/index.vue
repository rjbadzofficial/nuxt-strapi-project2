<template>
  <main>
    <div class="parallax" 
    :style="{background: `linear-gradient(0deg, rgba(0,118,163,.94) 9%, rgba(255,164,0,.42) 50%), url(${getMedia(homeParallaxBg)}) no-repeat fixed`}">
    </div>
    <div class="card-badges-container" :style="{background: `url(${getMedia(homeMainBg)})`}">
      <div class="banner-component-container">
        <MainBanner/>
      </div>
      <div class="carousel-container">
        <div class="sub-heading">
          <h2>A Partner <span>You Can Trust</span></h2>
          <hr class="carousel-title-hr">
        </div>
        <div class="carousel">
          <div class="container-fluid" v-if="cards.length">
            <VueSlickCarousel v-bind="settings" :slidesToShow="display">
              <div class="cards-container" v-for="card in cards" :key="card.id">
                <Card :fontawesome="card.fontawesome" :description="card.description"/>
              </div>
            </VueSlickCarousel>
          </div>
        </div>
      </div>
      <Cta :slug="'home'"/>
    </div>
  </main>
</template>

<script>
import { getMedia } from '~/utils/media'
import MainBanner from '~/components/banners/MainBanner.vue'
import Cta from '~/components/Cta.vue'
import VueSlickCarousel from 'vue-slick-carousel'
import Card from '~/components/cards/Card.vue'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default{
  components: {
    MainBanner,
    Cta,
    VueSlickCarousel,
    Card
  },
  data(){
    return {
      homeParallaxBg: '',
      homeMainBg: '',
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
  methods: {
    getMedia,
    onResize() {
      if(window.innerWidth < 443 + 15){
        this.display = 1
      }else if(window.innerWidth < 768 + 15){
        this.display = 2
      }else{
        this.display = 3
      }
    }
  },
  async fetch(){
    await this.$strapi.find('others', {slug: 'home-parallax'}).then(other => {
      this.homeParallaxBg = other[0].image.url
    })
    await this.$strapi.find('others', {slug: 'home-main'}).then(other => {
      this.homeMainBg = other[0].image.url
    })

    this.cards = await this.$strapi.find('cards')

  },
  mounted() {
    window.addEventListener("load", this.onResize);
    window.addEventListener("resize", this.onResize);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  }
  
}
</script>

<style scoped>
.sub-heading{
  text-align: center;
  margin-bottom: 3rem;
}
.parallax{
    height: 825px;
    background-position: center !important;
    background-size: cover !important;
}
.banner-component-container{
  position: relative;
  top: -42rem;
}
.card-badges-container{
  background-position: top !important;
  background-size: cover !important;
}
.carousel-container{
  margin-top: -38rem;
}
.carousel-title-hr{
  background-color: #00b6e6;
  width: 9rem;
  height: 0.5rem;
  margin: 0 auto;
  border: none;
  opacity: 1;
}
.carousel{
  margin-bottom: 4rem;
}
.container-fluid{
    max-width: 1100px;
    width: 100%;
}
.cards-container{
    text-align: center;
    box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.25);
    -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.25);
    -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.25);
    border-bottom: 0.5rem solid #00b6e6;
}
</style>

