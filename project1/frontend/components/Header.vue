<template>
    <header>
        <nav class="navbar navbar-expand-lg bg-light fixed-top">
            <div class="container-fluid">
                <nuxt-link class="navbar-brand" :to="{ path: '/'}">
                    <Logo :width="280" :src="logo[0].image.url" :alt="logo[0].title"/>
                </nuxt-link>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item dropdown" v-for="menu in menus" :key="menu.id">
                            <nuxt-link v-if="menu.submenus.length == 0" class="nav-link" :to="menu.path">{{menu.name}}</nuxt-link>
                            <a v-else class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                                {{menu.name}}
                            </a>
                        <ul class="dropdown-menu" v-if="menu.submenus">
                            <li v-for="submenu in menu.submenus" :key="submenu.id"><nuxt-link class="dropdown-item" :to="menu.path+submenu.path">{{submenu.name}}</nuxt-link></li>
                        </ul>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </header>
</template>

<script>
import Logo from '~/components/Logo.vue'
export default {
    components: {
        Logo
    },
    data(){
        return {
            logo: [],
            menus: []
        }
    },
    async fetch(){
        this.menus = await this.$strapi.find('menus')
        this.logo = await this.$strapi.find('logos', { slug: 'header' })
    }
}
</script>

<style scoped>

@media (min-width: 992px) {
    .navbar{
        height: 111px;
        background-color: #ffffff !important;
        box-shadow: 0px 0px 3px 0px rgba(0,0,0,0.25);
        -webkit-box-shadow: 0px 0px 3px 0px rgba(0,0,0,0.25);
        -moz-box-shadow: 0px 0px 3px 0px rgba(0,0,0,0.25);
    }
    .navbar-brand{
        position: relative;
        top: 1rem;
    }
    .container-fluid{
        width: 1110px;
    }
    .navbar-collapse{
        flex-grow: 0;
    }
    .navbar-nav a, .navbar-nav a:hover, .navbar-nav a:focus{
        color: #0076a3;
    }
    .nav-link{
        padding-left: 1.5rem !important;
        padding-right: 1.5rem !important;
    }
    .dropdown-menu{
        padding: 0;
    }
}
</style>