<script>
  import { subscribe } from "svelte/internal";
  import TodoItem from "./TodoItem.svelte";
  let todos = [
    { text: "create todo app in svelte", done: true },
    { text: "earn one million dollars", done: false },
  ];

  let todo = "";

  $: hasText = todo !== "";

  function handleAdd() {
    if (hasText) {
      todos = [...todos, { text: todo, done: false }];
      todo = "";
    }
  }

  function handleDelete(index) {
    todos.splice(index, 1);
    todos = todos;
  }

  function handleComplete(index) {
    todos[index].done = !todos[index].done;
  }
</script>

<form>
  <label for="todo" />
  <input type="text" bind:value={todo} placeholder="new todo" />
  <input
    type="submit"
    on:click|preventDefault={handleAdd}
    class={hasText ? "has-text" : "no-text"}
  />
</form>

<ul>
  {#each todos as todo, index}
    <TodoItem {todo} {index} {handleDelete} {handleComplete} />
  {/each}
</ul>

<style>
  ul {
    list-style-type: none;
  }
  .has-text {
    background-color: green;
  }
  .no-text {
    display: none;
  }
</style>
