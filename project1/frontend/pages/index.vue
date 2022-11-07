<template>
  <main>
    <div class="parallax" 
    :style="{backgroundImage: `url(http://localhost:1337${others[0].image.url})`}">
    </div>
    <Banner/>
  </main>
</template>

<script>
import Banner from '~/components/Banner.vue'
export default{
  components: {
    Banner
  },
  data(){
    return {
      others: []
    }
  },
  async fetch(){
    this.others = await this.$strapi.find('others')
    console.log(this.others)
  }
}
</script>

<style scoped>
.parallax{
    background: rgb(0,182,230);
    background-attachment: fixed;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    height: 750px;
}
</style>