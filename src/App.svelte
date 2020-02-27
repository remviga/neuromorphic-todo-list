<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";

  import TextField from "./components/neumorph/TextField/index.svelte";
  import Button from "./components/neumorph/Button/index.svelte";
  import Checkbox from "./components/neumorph/Checkbox/index.svelte";
  import Output from "./components/neumorph/Output/index.svelte";
  import Modal from "./components/Modal/index.svelte";
  import Title from "./components/MainTitle/index.svelte";

  import removeIcon from "./assets/icons/remove.png";

  let todos = [];
  let todoName = "";
  let confirmationModalIsVisible = false;
  let completionModalIsVisible = false;

  const onSubmit = () => {
    if (todos.some(t => t.name === todoName)) {
      confirmationModalIsVisible = true;
      return;
    }
    addTodo(todoName);
  };

  const addTodo = todoName => {
    if (todoName) {
      const todoTemplate = {
        id: Date.now(),
        name: todoName,
        completed: false
      };
      todos = [...todos, todoTemplate];
    }
  };

  const onRemove = id => {
    if (id !== undefined) {
      todos = todos.filter(t => t.id !== id);
    }
  };

  const confirmCreation = _ => {
    addTodo(todoName);
    confirmationModalIsVisible = false;
  };

  const cancelCreation = _ => (confirmationModalIsVisible = false);

  $: if (todos.length && todos.every(t => t.completed)) {
    completionModalIsVisible = true;
  }
</script>

<style lang="scss">
  main {
    max-width: 600px;
    margin: 0 auto;
    padding: 16px;
    min-height: 100vh;
    box-sizing: border-box;
  }
  .list {
    list-style: none;
    padding: 0;
    &-item {
      margin-bottom: 15px;
      &.completed {
        opacity: 0.5;
      }
      &:last-child {
        margin-bottom: 0;
      }
    }
  }
  .todo {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>

<main>
  <form on:submit|preventDefault={onSubmit}>

    <TextField bind:bindedValue={todoName} />
    <Button type="submit">Add</Button>

    <Title bind:todosLength={todos.length} />

    {#if todos.length}
      <ul class="list">
        {#each todos as todo}
          <li class="list-item" transition:fade={{ duration: 200 }}>
            <div class="todo" class:completed={todo.completed}>
              <Checkbox bind:checked={todo.completed} label={todo.name} />
              <Button
                type="button"
                onClick={_ => onRemove(todo.id)}
                icon={removeIcon} />
            </div>
          </li>
        {/each}
      </ul>
    {/if}

  </form>

  {#if confirmationModalIsVisible}
    <Modal onOutsideClick={cancelCreation}>
      <section>
        <h2>It looks like you already have this item</h2>
        <h3>Are you sure you want to add it?</h3>
        <Button onClick={confirmCreation}>Add</Button>
        <br />
        <Button onClick={cancelCreation}>Cancel</Button>
      </section>
    </Modal>
  {/if}

  {#if completionModalIsVisible}
    <Modal onOutsideClick={_ => (completionModalIsVisible = false)}>
      <section>
        <h2>All your todos are completed</h2>
        <Button onClick={_ => (completionModalIsVisible = false)}>Ok</Button>
      </section>
    </Modal>
  {/if}

</main>
