<script>
  import AddTodo from './AddTodo.svelte';
  import TodoItem from './TodoItem.svelte';
  let name = "John Doe";
  let todos = []
  const addTodo = e => {
    const todo = e.detail;
    todo.id = todos.length == 0 ? 0 : todos[0].id+1
    todos = [todo, ...todos]
  }
  const deleteTodo = e => {
    const id = e.detail;
    todos = todos.filter(t => t.id !== id);
  }
  const checkTodo = e => {
    const id = e.detail;
    let todo = todos.filter(t => t.id == id)
    let index  = todos.indexOf(todo);
    todo[0].checked = !todos[0].checked;
    todos[index] = todo;
  }
</script>

<div class="container mt-5">
  <div class="card">
    <div class="card-header bg-success text-white">
      <h1>Add Todo</h1>
    </div>
    <div class="card-body">
      <AddTodo on:addtodo={addTodo}/>
      {#if todos.length > 0}
        <br/>
         <ul class="list-group">
          {#each todos as todo}
            <TodoItem todo={todo} on:deletetodo={deleteTodo} on:checktodo={checkTodo} />
          {/each}
        </ul>
      {/if}
    </div>
  </div>
</div>

<style>

</style>