<script>
export let todoValue;
export let addTodo;
export let onChangeInput;
export let resetTodo;

</script>
<style></style>

<div class="todo-input-wrap">
  <input type="text" bind:value={todoValue} placeholder="enter todo" on:keyup={onChangeInput}>
  <input type="button" value="ADD" on:click={addTodo}>
  <input type="button" value="RESET" on:click={resetTodo}>
</div>