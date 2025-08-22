<script>
  let { newTodo, onInput, onAdd } = $props();
</script>

<label for="todo-input">New Todo:</label>
<input id="todo-input" bind:value={newTodo} oninput={onInput} />
<button onclick={onAdd}>Add Todo</button>
