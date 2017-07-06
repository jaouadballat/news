<template>
  <div id="app">
    <sourceSelection v-on:listArticles="articlesList"></sourceSelection>
    <newsList :articles="articles"></newsList>
  </div>
</template>

<script>
import sourceSelection from './components/sourceSelection.vue'
import newsList from './components/newsList.vue'

export default {
  name: 'app',
  components:{
    sourceSelection,
    newsList
  },
  data () {
    return {
      articles:[]
    }
  },
  methods:{
    articlesList(id){
     
      this.$http.get('https://newsapi.org/v1/articles?source='+id+'&sortBy=top&apiKey=c458fff76e414e449071fdf682eea249').then(data => {
        this.articles=data.body.articles
      })
    }
  }
}
</script>

<style>
#app {
}
</style>
