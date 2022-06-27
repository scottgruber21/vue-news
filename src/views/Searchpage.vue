<template>
<div v-if="loading">
  <h2>Loading...</h2>
</div>
  <NewsItem v-for="(story, index) in stories" :story="story" :isLast="index < storiesLength-1" :key="index"/>
</template>

<script>
// @ is an alias to /src
import NewsItem from '../components/NewsItem.vue'

export default {
  name: 'Searchpage',
  components: {
    NewsItem
  },
  data(){
    return {
      stories: [],
      loading: false,
      searchTerm: ''
    }
  },

    props: {
    numArticles: Number
  },
  watch: {
    numArticles(newVal, oldVal){
      this.loadStories(this.$route.params.term)
    }
  },
  methods: {
    async loadStories(term){
      this.loading = true
      this.searchTerm = term
      let res = await fetch(`https://newsapi.org/v2/everything?q=${this.searchTerm}&sortBy=popularity&apiKey=${process.env.VUE_APP_SECRET}&pageSize=${this.numArticles}`)
      let data = await res.json()
      this.stories = data.articles
      this.loading = false
    }
  },
 
 created(){
      this.loadStories(this.$route.params.term)
 },

beforeRouteUpdate(to, from){
  this.loadStories(to.params.term)
},
 
  computed:{
    storiesLength(){
      return this.stories.length
    }
  },
}
</script>
