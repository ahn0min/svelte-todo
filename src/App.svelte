<script>
	export let name;
  import TodoInput from './components/TodoInput.svelte'
  import TodoList from './components/TodoList.svelte'

  const DB = localStorage;
  let todoValue = ""
  let todos = DB.todos === undefined ? [] : JSON.parse(DB.todos);

  let addTodo = () => {
    if (!todoValue) return;

    const newTodo = { id: ++lastId, text: todoValue, checked: false }
    todos = [...todos, newTodo]
    todoValue = "";
    DB.todos = JSON.stringify(todos)
  }

  let handleChecked = (id) => {
    const index = todos.findIndex(todo => todo.id === id)
    todos[index]["checked"] = !todos[index]["checked"]

    DB.todos = JSON.stringify(todos);
  }

  let onChangeInput = e => {
    todoValue = e.target.value;

    if (e.keyCode === 13) {
      addTodo();
    }
  };

  let resetTodo = () => {
    todos = [];
    DB.removeItem('todos');
  }

  $: lastId = 0 || todos.length;

</script>

<main>
	<h1>{name} Todo!</h1>
  <TodoInput todoValue={todoValue} addTodo={addTodo} onChangeInput={onChangeInput} resetTodo={resetTodo} />
  <TodoList todos={todos} {handleChecked} />
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 100%;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
