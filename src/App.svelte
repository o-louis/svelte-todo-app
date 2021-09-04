<script>
	import Task from './components/Task.svelte';
	import Input from './components/Input.svelte';
	import TaskList from './components/TaskList.svelte';

	let tasks = [];
	let error = false;
	let task = { id: -1, name: '', completed: false }

	$: tasksRemaining = tasks.filter(task => !task.completed).length;

	const addTask = () => {
		error = !isDataValid(task)
		if (!error) {
			tasks = [
				...tasks,
				{
					id: tasks.length,
					name: task.name,
					completed: false,
				}
			];
			task = { id: -1, name: '', completed: false }
		}
	}

	const deleteTask = (event) => {
		tasks = tasks.filter(task => task.id !== event.detail.id);
	}

	const toggleCompleted = (event) => {
		const index = tasks.findIndex(task => task.id === event.detail.id);
		tasks[index].completed = !tasks[index].completed;
	}

	const isDataValid = ({ name }) => {
		return name.trim() && name !== '';
	}
</script>

<main>
	<h1>Svelte Todo App</h1>
	<p>{tasksRemaining} items left</p>

	<TaskList class="list">
		{#each tasks as task (task)}
			<Task {...task} on:delete={deleteTask} on:toggle={toggleCompleted} />
		{/each}
	</TaskList>

	<form on:submit|preventDefault={addTask}>
		<Input forID="task" label="Enter a task" bind:value={task.name} />
		{#if error}
			<span>Input field should not be empty</span>
		{/if}
	</form>
</main>

<style>
	h1 {
		text-align: center;
		padding: 1rem 1.5rem;
		border-bottom: 2px solid white;
	}
	p {
		padding: 1rem 0;
	}
	main {
		display: flex;
		flex-direction: column;
		align-items: stretch;
		width: 500px;
		background-color: #fafafa;
		padding: 1.5rem 2rem;
		box-shadow: 0 20px 30px 0 rgba(1, 1, 1, 0.07);
		margin: 6rem 0;
		border-radius: .75rem;
		background: #242424;
		color: white;
	}
</style>