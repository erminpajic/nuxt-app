<template>
	<section class="recipes">
		<Recipe
			v-for="recipe in recipes"
			:key ="recipe.id"
			:thumbnail="recipe.thumbnail"
			:title="recipe.title"
			:id="recipe.id"
			:previewText="recipe.previewText"
		/>

	</section>
</template>

<script>
	import Recipe from '@/components/Recipe'

	export default{
		components:{
			Recipe
		},
		asyncData(){
			return new Promise ((resolve, reject) => {
				setTimeout(() => {
					resolve({
						recipes:[
							{
								id: "1",
								title: "Delicious Pizza",
								previewText: "Awesome Pizza",
								thumbnail: "https://static.toiimg.com/thumb/53110049.cms?width=1200&height=900",
							},
							{
								id: "2",
								title: "Delicious Pizza 2",
								previewText: "Awesome Pizza 2",
								thumbnail: "https://static.toiimg.com/thumb/56933159.cms?imgsize=686279&width=800&height=800",
							}
						]
					})
				}, 1500);
			})
		}
	}
</script>

<style scoped>
	.recipes{
		display: flex;
		flex-flow: row wrap;
		justify-content: center;
		align-items: center;
	}
</style>