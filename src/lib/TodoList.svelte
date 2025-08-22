<script>
  import TodoInput from './TodoInput.svelte';
  import TodoItem from './TodoItem.svelte';
  import TodoListFilters from './TodoListFilters.svelte';

  let id = 0;
  let newTodo = $state('');
  let todos = $state([
    { id: id++, text: 'Learn HTML', done: true },
    { id: id++, text: 'Learn JavaScript', done: false },
    { id: id++, text: 'Learn Svelte', done: false }
  ]);
  let hideCompleted = $state(false);

  function addTodo() {
    if (newTodo.trim()) {
      todos.push({ id: id++, text: newTodo, done: false });
      newTodo = '';
    }
  }

  function inputHandler(e) {
    newTodo = e.target.value;
  }

  function toggleTodo(todo) {
    todo.done = !todo.done;
  }

  function removeTodo(todoId) {
    const idx = todos.findIndex(todo => todo.id === todoId);
    if (idx !== -1) {
      todos.splice(idx, 1);
    }
  }

  function toggleHideCompleted() {
    hideCompleted = !hideCompleted;
  }

  let visibleTodos = $derived(
    hideCompleted
      ? todos.filter(todo => !todo.done)
      : todos
  );
</script>

<h1>Svelte Todo List</h1>
<TodoInput
  {newTodo}
  onInput={inputHandler}
  onAdd={addTodo}
/>

<TodoListFilters
  {hideCompleted}
  onToggle={toggleHideCompleted}
/>

<ul>
  {#each visibleTodos as todo (todo.id)}
    <TodoItem
      {todo}
      onToggle={toggleTodo}
      onRemove={removeTodo}
    />
  {/each}
</ul>
