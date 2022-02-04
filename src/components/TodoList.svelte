<script>
  export let todos;
  export let handleChecked

  import TodoItem from "./TodoItem.svelte"
</script>

<style>
  div {
    display: flex;
  }
  ul {
    margin: 0 auto;
    padding: 0;
  }
</style>

<div>
  {#if todos === []}
    <li>추가해주세요</li>
  {:else}
    <ul>
      {#each todos as todo, i (todo.id)}
        <TodoItem todo={todo} {handleChecked} />
      {/each}
    </ul>
  {/if}
</div>