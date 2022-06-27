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
  name: 'UKView',
  components: {
    NewsItem
  },
  data(){
    return {
      stories: [],
      loading: false
    }
  },

watch: {
    numArticles(newVal, oldVal){
      this.loadStories()
    }
  },

  methods: {
    async loadStories(){
      this.loading = true
      let fetchUrl = 'https://newsapi.org/v2/top-headlines?country=gb&apiKey=' + process.env.VUE_APP_SECRET + '&pageSize=' + this.numArticles
      let res = await fetch(fetchUrl)
      let data = await res.json()
      this.stories = data.articles
      this.loading = false
    }
  },

  props: {
    numArticles: Number
  },


 created(){
  this.loadStories()
 },

 
  computed:{
    storiesLength(){
      return this.stories.length
    }
  },
}
</script>
