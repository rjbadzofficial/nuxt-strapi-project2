<template>
    <main>
        <ProductBanner :slug="slug"/>
        <div class="main_data">
            <div class="container-fluid">
                <div class="sub_title">
                    <h2>Healthcare Solutions</h2>
                    <hr/>
                </div>
                <div class="card_container">
                    <HealthcareCard v-for="healthcare in healthcares" :key="healthcare.id" :right="right = !right"
                    :title="healthcare.title"
                    :description="healthcare.description"
                    :imageUrl="healthcare.image.url"
                    :link="healthcare.path"
                />
                </div>
        </div>
        </div>
        <Cta :slug="slug"/>
    </main>
</template>

<script>
import ProductBanner from '~/components/banners/ProductBanner.vue'
import Cta from '~/components/Cta.vue'
import HealthcareCard from '~/components/cards/HealthcareCard.vue'
export default {
    data(){
        return {
            slug: 'healthcare',
            healthcares: [],
            right: false
        }
    },
    components: {
        ProductBanner,
        Cta,
        HealthcareCard
    },
    async fetch(){
        this.healthcares = await this.$strapi.find('healthcares')
    }
}
</script>

<style scoped>
.container-fluid{
    max-width: 1110px;
    width: 100%;
}
.sub_title{
    text-align: center;
    margin-bottom: 5rem;
}
.sub_title h2{
    font-size: 2.5rem;
}
.sub_title hr{
    opacity: 1;
    border: 4px solid #00b6e6;
    width: 10rem;
    margin: 0 auto;
}
.card_container{
    width: 100%;
    display: flex;
    align-items: center;
    gap: 3rem;
}
@media (max-width: 810px) {
    .card_container{
        flex-direction: column;
    }
}
</style>