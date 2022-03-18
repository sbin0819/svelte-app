<script>
  export let todo;
  export let idx;
  export let removeTodo;
</script>

<div
  class={`flex items-center px-4 h-12 border-dashed ${
    idx !== 0 && 'border-t-2 border-green-100'
  } justify-between`}
>
  <span>{todo}</span>
  <span class="cursor-pointer" on:click={() => removeTodo(idx)}>X</span>
</div>
