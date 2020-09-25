<template>
	<div id="app">
		<h1>Tarefas</h1>
		<TaskProgress :progress="progress" />
		<NewTask @taskAdded="addTask"/> 
		<TaskGrid 
		@taskDeleted="deleteTask" 
		@taskStateChanged="toggleTaskState"
		:tasks="tasks"/>
		
	</div>
</template>

<script>
import TaskGrid from './Components/TaskGrid'
import NewTask from './Components/NewTask'
import TaskProgress from './Components/TaskProgress'

export default {
	components: {TaskGrid, NewTask, TaskProgress},
	data(){
		return {
			tasks: [
				{name: 'Ir ao mercado', pending: true},
				{name: 'estudar para prova', pending: false}
			]
		}
	},
	computed: {
		progress() {
			const total = this.tasks.length
			const done = this.tasks.filter(t => !t.pending).length
			return Math.round(done / total * 100) || 0
		}
	},
	watch: {
		tasks: {
			deep: true, 
			handler() {
				localStorage.setItem('tasks', JSON.stringify(this.tasks))

			}
		}
	},
	methods: {
		addTask(task){ //chamada de função registrada na linha 4
			const sameName = t => t.name === task.name  //verificação de nomes iguais na lista
			const reallyNew = this.tasks.filter(sameName).length == 0
			if(reallyNew) { //se não estiver ele usa o metodo push para adicionar um novo valor 
				this.tasks.push({
					name: task.name,
					pending: task.pending || true })
			}
		}, 
		deleteTask(i) {
			this.tasks.splice(i, 1)
		},
		toggleTaskState(i) {
			this.tasks[i].pending = !this.tasks[i].pending
		}
		
	}, 
	created(){
		const json = localStorage.getItem('tasks')
		const array = JSON.parse(json)
		this.tasks = Array.isArray(array) ? array : []
	}

}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to bottom, #fc4a1a, #f7b733);
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
