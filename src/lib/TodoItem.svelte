<script>
  let { todo, onToggle, onRemove } = $props();
</script>

<li>
  <input type="checkbox" checked={todo.done} onchange={() => onToggle(todo)} />
  <span>{todo.text}</span>
  <button onclick={() => onRemove(todo.id)}>X</button>
</li>
