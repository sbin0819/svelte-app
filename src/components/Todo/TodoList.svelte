<script lang="ts">
  import '../../assets/app.css';
  import TodoItem from './TodoItem.svelte';

  let todo = '';
  let todos: string[] = [];

  function addTodo() {
    todos.push(todo);
    todos = todos;
    todo = '';
  }

  function removeTodo(id: string) {
    todos.splice(+id, 1);
    todos = todos;
  }
</script>

<div class="flex justify-center">
  <div class="flex flex-col items-center w-4/5">
    <div>
      <h1 class="text-4xl text-green-500">TodoList</h1>
    </div>
    <div class="w-3/5 min-w-[300px] mt-4">
      <form on:submit|preventDefault={addTodo}>
        <input
          class="px-4 shadow-lg w-full h-12 rounded-lg"
          bind:value={todo}
        />
      </form>
    </div>
    {#if todos.length > 0}
      <div
        class="bg-slate-50 w-3/5 min-w-[300px] mt-4 border-solid border-[1px] border-green-200 rounded-sm"
      >
        {#each todos as todo, i (i)}
          <TodoItem {todo} idx={i} {removeTodo} />
        {/each}
      </div>
    {/if}
  </div>
</div>
