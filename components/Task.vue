<template>
	<div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
		<h3>
			{{ task.text }}
			<span @click="$emit('delete-task', task.id)" class="cross"></span>
		</h3>
		<p>{{ task. day }}</p>
	</div>
</template>

<script>
export default {
	name: 'Task',
	props:{
		task: Object
	},
}
</script>

<style scoped>
.task{
	background: #f4f4f4;
	position: relative;
	margin: 5px;
	padding: 10px 20px;
	cursor: pointer;
}
.task.reminder{
	border-left: 5px solid green;
}
.task h3{
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.cross{
	position: absolute;
	right: 20px;
	top: 10px;
	width: 16px;
	height: 16px;
}
.cross:before{
	content: "";
	position: absolute;
	transform: rotate(45deg);
	background: red;
	width: 16px;
	height: 2px;
	top: 7px;
}
.cross:after{
	content: "";
	position: absolute;
	transform: rotate(-45deg);
	background: red;
	width: 16px;
	height: 2px; 
	top: 7px;
}
</style>