<script>
  export let todo;
  export let index;
  export let handleComplete;
  export let handleDelete;
</script>

<li>
  <p
    on:click={handleComplete(index)}
    class={!todo.done ? "is-not-done" : "is-done"}
  >
    {todo.text}
  </p>
  <button
    on:click={() => handleComplete(index)}
    class={todo.done ? "btn-is-done" : "btn-is-not-done"}
  >
    {todo.done ? "❌" : "✔"}
  </button>
  <button on:click={() => handleDelete(index)} class="delete">🗑</button>
</li>

<style>
  li * {
    display: inline;
  }
  button {
    font-weight: bolder;
  }
  .is-done {
    text-decoration: line-through;
    text-decoration-style: double;
    color: green;
    font-weight: bold;
  }
  .is-not-done {
    color: red;
  }
  .delete {
    background-color: rgba(255, 0, 0, 0.7);
  }
  .btn-is-done {
    background-color: royalblue;
  }
  .btn-is-not-done {
    background-color: green;
  }
  p:hover,
  button:hover {
    cursor: pointer;
  }
</style>
