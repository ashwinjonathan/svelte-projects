<script lang=ts>
	let todos = $state([
		{ id: 1, text: 'Buy Groceries', done: false },
		{ id: 2, text: 'Build an application', done: false },
		{ id: 3, text: 'Download the album', done: false },
	])

	let newTodoText = $state('');

	function addTodo(){
		if (newTodoText.trim() === '') return;

		todos.push({
			id : Math.floor(Math.random() * 1000000),
			text : newTodoText,
			done : false
		});

		newTodoText = '';
	}
		
		function deleteToDo(id: number){
		todos = todos.filter(t => t.id !== id)
	}
</script>

<input bind:value={newTodoText} placeholder="What needs to be done?" />
<button onclick={addTodo}>Add</button>

<ul>
	{#each todos as todo (todo.id)}
		<li>
			<input type="checkbox" bind:checked={todo.done}>
			<span>{todo.text}</span>
			<button onclick={() => deleteToDo(todo.id)}>Delete</button> 
		</li>
	{/each}
</ul>

<p>{todos.filter (t => !t.done).length} remaining</p>