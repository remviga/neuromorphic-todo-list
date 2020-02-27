<script>
  import { fade } from "svelte/transition";
  export let onOutsideClick = _ => {};
</script>

<style lang="scss">
  .modal-overlay {
    z-index: 10;
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.5);
  }
  .modal-instance {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 16px;
    box-sizing: border-box;
    height: 100%;
  }
  .modal-card {
    padding: 16px;
    background: #c5cdd4;
    border-radius: 5px;
  }
</style>

<article class="modal-overlay">
  <section class="modal-instance" on:click={onOutsideClick}>
    <div class="modal-card" in:fade={{ duration: 200 }}>
      <slot />
    </div>
  </section>
</article>
