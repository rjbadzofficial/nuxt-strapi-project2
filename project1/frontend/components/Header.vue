<template>
    <header>
        <nav class="navbar navbar-expand-lg bg-light fixed-top">
            <div class="container-fluid">
                <a class="navbar-brand" href="#"><Logo :width="280"/></a>
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
            menus: []
        }
    },
    async fetch(){
        this.menus = await this.$strapi.find('menus')
    }
}
</script>

<style scoped>

@media (min-width: 992px) {
    .navbar{
        height: 111px;
    }
    .container-fluid{
        width: 1110px;
    }
    .navbar-collapse{
        flex-grow: 0;
    }
}
</style>