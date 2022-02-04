<script>
  export let todo
  export let handleChecked
</script>

<style>
  li {
    width: 50vw;
    max-width: 500px;

    font-weight: bold;
    border: 1px solid #a8a4a4;
    border-radius: 5px;
    padding: 20px;

    margin: 5px;
    text-align: left;
    list-style: none;
  }

  .todo-item--checked {
    background-color: #ff4000d7;
    color: ivory
  }

</style>

<li class:todo-item--checked={todo.checked} on:click={() => handleChecked(todo.id)}>{todo.text}</li>