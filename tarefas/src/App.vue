<template>
	<div id="app">
		<h1>Tarefas</h1>
		<TaskGrid :tasks="tasks"/>
	</div>
</template>

<script>
import TaskGrid from './Components/TaskGrid'
export default {
	components: {TaskGrid},
	data(){
		return {
			tasks: [
				{name: 'Ir ao mercado', pending: true},
				{name: 'estudar para prova', pending: false}
			]
		}
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
