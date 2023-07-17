<template>
    <nav class="sidebar">
        <header>
            <div class="image-text">
                <span class="image">
                    <img src="https://companieslogo.com/img/orig/ABNB-4aaade0f.png?t=1633511992" alt="logo">
                </span>

                <div class="text header-text">
                    <span class="name"><strong> Cannavaro Yogi </strong></span>
                    <span class="role"><strong> Member </strong></span>
                </div>
            </div>
            <i class="bx bx-chevron-right toggle"></i>
        </header>

        <div class="menu-bar">
            <div class="menu">
                <li class="search-box">
                    <i class="bx bx-search icon"></i>
                    <input class="search" type="search" placeholder="Search...">
                </li>
                <li class="nav-links">
                    <router-link ref="dashboardLink" class="nav-link link-dashboard" to="/">
                    <i class="bx bx-home-alt icon"></i><span class="text nav-text"><strong>Home</strong></span>
                    </router-link>
                </li>
                <li class="nav-links">
                    <router-link class="nav-link link-dashboard" to="/">
                    <i class="bx bx-book-alt icon"></i><span class="text nav-text"><strong>Comics</strong></span>
                    </router-link>
                </li>
            </div>
        </div>

        <footer>
        <div class="menu-bottom">
            <li class="nav-links">
                <router-link class="nav-link link-dashboard" to="/">
                <i class="bx bx-log-out icon"></i><span class="text nav-text"><strong>Logout</strong></span>
                </router-link>
            </li>
        </div>
        </footer>
    </nav>
</template>

<script>
import router from '@/router';

export default {
    name: 'SideBar',
    methods : {
        isRouteActive() {
           return router.currentRoute.path === '/';
        },
        isRouteActiveComics() {
            return router.currentRoute.path == '/comics';
        },
        toggleActiveClass() {
            const dashboardLink = this.$refs.dashboardLink.$el;
            const spanElement = dashboardLink.querySelector('span');
            const iconElement = dashboardLink.querySelector('i');
            if (this.isRouteActive()) {
            dashboardLink.classList.add('bg-dash');
            spanElement.classList.add('bg-dash');
            iconElement.classList.add('bg-dash');
            } else {
            dashboardLink.classList.remove('bg-dash');
            spanElement.classList.remove('bg-dash');
            iconElement.classList.remove('bg-dash');
            }
        }
    },
    mounted() {
        this.toggleActiveClass(); // Call it on component mount or whenever needed
    }

}
</script>

<style>

</style>