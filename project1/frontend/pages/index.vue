<template>
  <main>
    <div class="parallax" 
    :style="{background: `linear-gradient(0deg, rgba(0,118,163,.94) 9%, rgba(255,164,0,.42) 50%), url(http://localhost:1337${others[0].image.url}) no-repeat fixed`}">
    </div>
    
    <div class="card-badges-container" :style="{background: `url(http://localhost:1337${others[1].image.url})`}">
      <Banner class="banner-component"/>
      <div class="carousel-container">
        <h2 style="text-align: center">A Partner <span>You Can Trust</span></h2>
        <hr class="carousel-title-hr">
        <!-- <Carousel/> -->
      </div>
    </div>
  </main>
</template>

<script>
import Banner from '~/components/Banner.vue'
import Carousel from '~/components/Carousel.vue'
export default{
  components: {
    Banner,
    Carousel
  },
  data(){
    return {
      others: []
    }
  },
  async fetch(){
    this.others = await this.$strapi.find('others')
  }
}
</script>

<style scoped>
.parallax{
    height: 825px;
    background-position: center !important;
    background-size: cover !important;
}
.banner-component{
  position: relative;
  top: -35rem;
}
.card-badges-container{
  background-position: top !important;
  background-size: cover !important;
}
.carousel-container{
  margin-top: -30rem;
}
.carousel-title-hr{
  background-color: #00b6e6;
  width: 9rem;
  height: 0.5rem;
  margin: 0 auto;
  border: none;
  opacity: 1;
}
</style>