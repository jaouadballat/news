<template>
	<div id="sourceSelection" class="container">
		<div class="jumbotron">
			<h1><i class="glyphicon glyphicon-th-list"></i> News List</h1>		
			<h3>Select News Source</h3>	
			<form class="form-horizontal">
				<select v-model = "source" v-on:change="sourceChanged" class="form-control">
					<option value="1">Select a resource</option>
					<option :value="source" v-for="source in sources">{{ source.name }}</option>
				</select>
				<div v-if="source !=1">
					<h5 class="text-muted">{{source.description}}</h5>
					<a class="btn btn-primary" :href="source.url" target="_blank">Go To {{ source.name }}</a>
				</div>
			</form>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return {
				sources:[],
				source:'1'
			}
		},
		created(){
			this.$http.get('https://newsapi.org/v1/sources?language=en&apikey=c458fff76e414e449071fdf682eea249').then(data => {
				this.sources = data.body.sources
				//console.log(data)
			})
		},
		methods:{
			sourceChanged(){
				this.$emit('listArticles', this.source.id)
			}
		}
	}
</script>

<style>
	
</style>