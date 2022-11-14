<template>
    <footer>
        <div class="container-fluid logo-info-container">
            <div class="row logo-info-row">
                <div class="col-md-5 logo-container">
                    <Logo :width="200" :src="logos[1].image.url" :alt="logos[1].title"/>
                </div>
                <div class="infos-container col-md-7">
                    <div class="row">
                        <div class="col-md-6 info-container" v-for="info in infos" :key="info.id">
                            <div class="subheading">{{info.title}}</div>
                            <p class="content">{{info.content}}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="copyright">
            <div class="container-fluid">
                <div class="row">
                    <div class="col-md-6">&copy;2021 Caracal - All rights reserved.</div>
                    <div class="col-md-6">
                        <span>Privacy Policy</span><span> | </span>
                        <span>Terms of Use</span><span> | </span>
                        <span>Accessibility</span>
                    </div>
                </div>
            </div>
        </div>
    </footer>
</template>

<script>
import Logo from '~/components/Logo.vue'
export default{
    components: {
        Logo
    },
    data(){
        return {
            logos: [],
            infos: []
        }
    },
    async fetch(){
        this.logos = await this.$strapi.find('logos')
        this.infos = await this.$strapi.find('infos')
    }
}
</script>

<style scoped>
.logo-info-container{
    padding: 1rem;
}
.copyright{
    background-color: #0076a3;
    color: #ffffff;
    padding: 1rem;
    margin-top: 4rem;
}
.subheading{
    color: #0076a3;
    font-weight: bold;
    font-size: 18px;
}

@media (min-width: 992px) {
    .container-fluid{
        max-width: 1110px;
        width: 100%;
    }
}
@media (min-width: 768px) {
    .logo-info-row{
        padding-top: 4rem;
    }
}
@media (max-width: 767px) {
    footer{
        margin-top: 4rem;
    }
    .logo-container{
        display: flex;
        justify-content: center;
    }
    .infos-container{
        margin-top: 4rem;
    }
    .info-container{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .copyright{
        text-align: center;
    }
}
</style>