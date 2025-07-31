<script>
  let { hideCompleted, onToggle } = $props();
</script>

<label>
  <input type="checkbox" bind:checked={hideCompleted} onchange={onToggle} />
  Hide completed
</label>
