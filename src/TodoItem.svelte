<script>
  import { createEventDispatcher } from 'svelte'; 
  const dispatch = createEventDispatcher();
  export let todo;
  const onClick = () => {
    dispatch("deletetodo", todo.id);
  }
  const onCheck = () => {
    dispatch("checktodo", todo.id);
  }
</script>
<li class="list-group-item d-flex align-items-center justify-content-between">
  <div>
  <input type="checkbox" id="checked" checked={todo.checked} on:click={onCheck}>
    {#if !todo.checked} 
      {todo.title}
    {:else}
      <del>{todo.title}</del>
    {/if}
  </div>
  <button class="btn btn-danger float-right" on:click={onClick}>X</button>
</li>
