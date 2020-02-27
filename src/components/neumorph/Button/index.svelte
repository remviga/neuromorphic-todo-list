<script>
  export let icon = "";
  export let type = "button";
  export let onClick = () => {};
</script>

<style lang="scss">
  .btn {
    &:not(:disabled) {
      flex-grow: 1;
      flex-shrink: 0;
      width: 100%;
      font-weight: 600;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: sans-serif;
      color: #333;
      border-radius: 16px;
      background: transparent;
      z-index: 1;
      box-shadow: 5px 5px 10px #c5cdd4, -5px -5px 10px #ffffff;
      transition: box-shadow 0.2s ease;
      margin: 0;
    }

    &:disabled {
      opacity: 0.5;
    }

    &.icon {
      flex-basis: 50px;
      border-radius: 50%;
      max-width: 50px;
      min-height: 50px;
      width: 50px;
      height: 50px;
      box-shadow: 5px 5px 10px #d99a95, -5px -5px 10px #ffd0c9;
      &:before,
      &:after {
        border-radius: 50%;
      }
      img {
        max-width: 50%;
        opacity: 0.6;
      }
    }
    &:before,
    &:after {
      z-index: -1;
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      right: 0;
      bottom: 0;
      box-shadow: none;
      transition: opacity 0.1s ease;
      border-radius: 16px;
    }
    &:after {
      opacity: 0;
      background: linear-gradient(145deg, #d1d9e0, #f8ffff);
    }
    &:before {
      opacity: 1;
      background: linear-gradient(145deg, #f8ffff, #d1d9e0);
    }
    &:active:after {
      opacity: 1;
    }
  }
</style>

<button class="btn" class:icon {type} on:click={onClick}>
  {#if icon}
    <img src={icon} alt="" />
  {:else}
    <slot />
  {/if}
</button>
