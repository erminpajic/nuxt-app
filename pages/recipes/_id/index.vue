<template>
	<section class="single-recipe">
		<h1>{{ recipe.title }}</h1>
		<div>
			<img class="recipe-img" :src="recipe.thumbnail" :alt="recipe.title">
		</div>
		<p>{{ recipe.descriptionText }}</p>
	</section>
</template>

<script>
export default {
	asyncData(context){
		return new Promise ((resolve, reject) => {
			setTimeout(() => {
				resolve({
					recipe:[
						{
							id: "1",
							title: "Delicious Pizza",
							previewText: "Awesome Pizza",
							descriptionText: "proba lorem ipsum 123",
							thumbnail: "https://static.toiimg.com/thumb/53110049.cms?width=1200&height=900",
						},
						{
							id: "2",
							title: "Delicious Pizza 2",
							previewText: "Awesome Pizza 2",
							descriptionText: "proba lorem ipsum 123",
							thumbnail: "https://static.toiimg.com/thumb/56933159.cms?imgsize=686279&width=800&height=800",
						}
					].find(el => el.id === context.params.id)
				})
			}, 1500);
		})
	}
}
</script>

<style scoped>
	.single-recipe{
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		padding: 30px;
		flex-flow: column;
	}
	.recipe-img{
		width: 100%;
	}
</style>