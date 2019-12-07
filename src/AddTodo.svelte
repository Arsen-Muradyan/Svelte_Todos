<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  let todo = {
    title: '',
    checked: false
  }
  const onSubmit = (e) => {
    e.preventDefault(); 
    dispatch("addtodo", todo)
    // Clear todo
    todo = {
      id: null,
      title: '',
      checked: false
    }
  }
</script>
<form on:submit={onSubmit} class="form-inline">
  <input type="text" class="form-control mr-3" style="width: 90%" bind:value={todo.title}>
  <input type="submit" class="btn btn-secondary">
</form>