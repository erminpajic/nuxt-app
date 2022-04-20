<template>
	<div class="container">
		<Header @toggle-add-task="toggleAddTask" :showAddTask="showAddTask" title="Title Tracker" />
		<div v-show="showAddTask">
			<AddTask @add-task="addTask" />
		</div>
		<Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
		<Footer />
	</div>
</template>

<script>
import Header from '../components/Header'
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'
import Footer from '../components/Footer'

export default {
	name: 'App',
	components:{
		Header,
		Tasks,
		AddTask,
		Footer
	},
	data(){
		return{
			tasks: [],
			showAddTask: false
		}
	},
	methods:{
		toggleAddTask(){
			this.showAddTask = !this.showAddTask
		},
		addTask(task){
			this.tasks = [...this.tasks, task]
		},
		deleteTask(id){
			if(confirm('Are you sure')){
				this.tasks = this.tasks.filter((task) => task.id !== id)
			}
		},
		toggleReminder(id){
			this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder}: task)
		}
	},
	created(){
		this.tasks = [
			{
				id: 1,
				text: 'Doctors Appointment',
				day: 'March 1st at 2:30pm',
				reminder: false,
			},
			{
				id: 2,
				text: 'Meeting at school',
				day: 'March 3rd at 1:30pm',
				reminder: true,
			},
			{
				id: 3,
				text: 'Food Shopping',
				day: 'March 4th at 11:00am',
				reminder: false,
			},
		]
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
*{
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
body{
	font-family: 'Poppins, sans-serif';
}
.container{
	max-width: 500px;
	margin: 30px auto;
	overflow: auto;
	min-height: 300px;
	border: 1px solid green;
	padding: 30px;
	border-radius: 5px;
}
.btn{
	display: inline-block;
	background: #000;
	border: none;
	padding: 10px 20px;
	margin: 5px;
	border-radius: 5px;
	cursor: pointer;
	text-decoration: none;
	font-size: 15px;
	color: white;
	font-family: inherit;
}
.btn:focus{
	outline: none;
}
</style>