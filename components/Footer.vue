<template>
	<div class="footer">
		<ul>
			<li>Homepage</li>
			<li>Tasks</li>
			<li>Recipes</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: 'Footer',
	props: {
		title: String,
	}
}
</script>

<style scoped>
	ul{
		list-style: none; display: flex; align-items: center; justify-content: space-between; width: 100%;
	}
	li{text-decoration: none; text-transform: uppercase;}
	.footer{margin-top: 100px;}
</style>