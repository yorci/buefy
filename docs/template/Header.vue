<template>
    <!--Navbar has an issue with colored Hero-->
    <!--<header class="navbar is-transparent container">
        <div class="navbar-brand">
            <router-link to="/" exact class="navbar-item">
                <img v-if="home" src="../assets/buefy-light.png" alt="Buefy">
                <img v-else src="../assets/buefy.png" alt="Buefy">
            </router-link>

            <a class="navbar-item" href="https://github.com/rafaelpimpa/buefy" target="_blank">
                <b-icon pack="fa" icon="github"></b-icon>
            </a>

            <a class="navbar-item" href="https://twitter.com/rafaelpimpa" target="_blank">
                <b-icon pack="fa" icon="twitter"></b-icon>
            </a>

            <span class="navbar-burger burger"
                :class="{ 'is-active': isMenuActive }"
                @click="isMenuActive = !isMenuActive">
                <span></span>
                <span></span>
                <span></span>
            </span>
        </div>

        <div class="navbar-menu" :class="{ 'is-active': isMenuActive }">
            <div class="navbar-end">
                <router-link to="/" exact class="navbar-item">Home</router-link>

                <div class="navbar-item has-dropdown is-hoverable">
                    <router-link to="/documentation" class="navbar-link">Documentation</router-link>

                    <div class="navbar-dropdown">
                        <router-link to="/documentation/quick-start" class="navbar-item">Installation</router-link>
                        <router-link to="/documentation/layout" class="navbar-item">General</router-link>
                        <router-link to="/documentation/dialog" class="navbar-item">Notices</router-link>
                        <router-link to="/documentation/field" class="navbar-item">Form</router-link>
                        <router-link to="/documentation/table" class="navbar-item">Data</router-link>
                        <hr class="navbar-divider">
                        <div class="navbar-item has-text-grey">Version: {{ version }}</div>
                    </div>
                </div>

                <div class="navbar-item">
                    <a class="button is-outlined"
                        :class="home ? 'is-light' : 'is-twitter'"
                        @click="tweet">
                        <b-icon pack="fa" icon="twitter"></b-icon> <span>Tweet</span>
                    </a>
                </div>
            </div>
        </div>
    </header>-->

    <header class="nav">
        <div class="container">
            <div class="nav-left">
                <router-link to="/" exact class="nav-item is-brand">
                    <img v-if="home" src="../assets/buefy-light.png" alt="Buefy">
                    <img v-else src="../assets/buefy.png" alt="Buefy">
                </router-link>
            </div>
            <div class="nav-center">
                <a class="nav-item" href="https://github.com/rafaelpimpa/buefy" target="_blank">
                    <b-icon pack="fa" icon="github"></b-icon>
                </a>
                <a class="nav-item" href="https://twitter.com/rafaelpimpa" target="_blank">
                    <b-icon pack="fa" icon="twitter"></b-icon>
                </a>
            </div>

            <span class="nav-toggle"
                :class="{ 'is-active': isMenuActive }"
                @click="isMenuActive = !isMenuActive">
                <span></span>
                <span></span>
                <span></span>
            </span>

            <div class="nav-right nav-menu" :class="{ 'is-active': isMenuActive }">
                <router-link to="/" exact class="nav-item">Home</router-link>
                <router-link to="/documentation" class="nav-item">Documentation</router-link>

                <div class="nav-item">
                    <a class="button is-outlined"
                        :class="home ? 'is-light' : 'is-twitter'"
                        @click="tweet">
                        <b-icon pack="fa" icon="twitter"></b-icon>
                        <span>Tweet</span>
                    </a>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
    import Package from '../../package.json'

    export default {
        props: {
            home: Boolean
        },
        data() {
            return {
                isMenuActive: false,
                version: Package.version
            }
        },
        methods: {
            tweet() {
                const width = 575
                const height = 400
                const left = (window.screen.width - width) / 2
                const top = (window.screen.height - height) / 2
                const url = `https://twitter.com/share?url=${encodeURIComponent(document.location.protocol + '//' + document.location.host)}&text=Buefy: lightweight UI components for Vue.js based on Bulma&hashtags=buefy&via=rafaelpimpa`
                const opts = `status=1,width=${width},height=${height},top=${top},left=${left}`

                window.open(url, '', opts)
            }
        }
    }
</script>
