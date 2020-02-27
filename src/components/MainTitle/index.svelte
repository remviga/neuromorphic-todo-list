<script>
  import { fade } from "svelte/transition";
  export let todosLength = 0;
</script>

<style lang="scss">
  h1 {
    center {
      opacity: 0.5;
      font-size: 0.6em;
    }
  }
</style>

<h1>
  {#if todosLength}
    <span in:fade={{ duration: 2000 }}>Your todos</span>
  {:else}
    <span>
      <center>
        <i>Add your todos...</i>
      </center>
    </span>
  {/if}
</h1>
