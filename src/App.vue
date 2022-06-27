<template>
<div class="header">
<h1>News Today</h1>
</div>
<Searchbox @submitted="handleSearch" />
  <nav>
    <router-link class="routerLink" to="/">US</router-link>
    <router-link class="routerLink" to="/uk">UK</router-link>
  </nav>
  <div class="container">
      <NumArticles @numChange="x => numArticles = x" />
    <router-view :searchTerm="searchTerm" :numArticles="numArticles" />
  </div>
  <Footer @aboutOpen="aboutOpen=true" />
  <About v-if="aboutOpen" @aboutClose="aboutOpen = false" />
</template>

<script>
import Searchbox from './components/Searchbox.vue'
import NumArticles from './components/NumArticles.vue'
import Footer from './components/Footer.vue'
import About from './components/About.vue'

export default{
  components: {
    Searchbox,
    NumArticles,
    Footer,
    About
  },
  data(){
    return {
      searchTerm: '',
      numArticles: 10,
      aboutOpen: false
    }
  },
  methods: {
    handleSearch(x){
      this.searchTerm = x
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: steelblue;
}

.container, .header{
  padding: 0 30px;
  max-width: 1200px;
  margin: auto;
}

h1{
  text-align: left;
  font-family: 'EB Garamond', serif;
  font-size: 3rem;
}

nav .routerLink{
  font-size: 2.1rem;
  margin: 0 30px;
  text-decoration: none;
}

</style>
