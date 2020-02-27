<script>
  export let fullWidth = false;
</script>

<style lang="scss">
  .output {
    flex-shrink: 0;
    margin-right: 15px;
    display: flex;
    align-items: center;
    padding: 15px 10px;
    border-radius: 10px;
    background: #c5cdd4;
    box-shadow: 19px 19px 38px #a9b0b6, -19px -19px 38px #e1eaf2;
    &.full-width {
      flex: 1;
      flex-grow: 1;
    }
  }
</style>

<div class={fullWidth ? 'output full-width ' : 'output'}>
  <slot />
</div>
