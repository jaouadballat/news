<template>
	<div id="newsList" class="container">
		<div class="media" v-for="article in articles">
		  <div class="media-left">
		    <a :href="article.url" target="_blank">
		      <img class="media-object" :src="article.urlToImage">
		    </a>
		  </div>
		  <div class="media-body">
		    <a :href="article.url" target="_blank"><h4 class="media-heading">{{article.title}}</h4></a>
		    <p>{{article.description}}</p>
		  </div>
		</div>
	</div>
</template>

<script>
	export default{
		props:['articles'],
		data(){
			return {

			}
		}
	}
</script>

<style>
	img{
		max-height: 10%;
	}
</style>