<script>
  let { newTodo, onInput, onAdd } = $props();
</script>

<input bind:value={newTodo} oninput={onInput} />
<button onclick={onAdd}>Add Todo</button>
