<template>
    <main>
        <ProductBanner :slug="slug"/>
        <div class="main_data">
            
        </div>
        <Cta :slug="slug"/>
    </main>
</template>

<script>
import ProductBanner from '~/components/banners/ProductBanner.vue'
import Cta from '~/components/Cta.vue'
export default {
    data(){
        return {
            slug: 'signs'
        }
    },
    components: {
        ProductBanner,
        Cta
    }
}
</script>