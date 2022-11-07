<template>
    <header>
        <nav class="navbar navbar-expand-lg bg-light fixed-top">
            <div class="container-fluid">
                <a class="navbar-brand" href="#"><Logo :width="280" :src="logos[0].image.url" :alt="logos[0].title"/></a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item dropdown" v-for="menu in menus" :key="menu.id">
                            <a v-if="menu.submenus.length == 0" class="nav-link" href="#">{{menu.name}}</a>
                            <a v-else class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                                {{menu.name}}
                            </a>
                        <ul class="dropdown-menu" v-if="menu.submenus">
                            <li v-for="submenu in menu.submenus" :key="submenu.id"><a class="dropdown-item" href="#">{{submenu.name}}</a></li>
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
            logos: [],
            menus: []
        }
    },
    async fetch(){
        this.menus = await this.$strapi.find('menus')
        this.logos = await this.$strapi.find('logos')
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
}
</style>