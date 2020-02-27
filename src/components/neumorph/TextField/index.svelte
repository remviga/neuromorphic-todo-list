<script>
  export let bindedValue;
</script>

<style lang="scss">
  .text-field {
    display: block;
    width: 100%;
    padding: 15px;
    border: 0;
    text-align: center;
    appearance: none;
    box-sizing: border-box;
    font-weight: 600;
    color: #333;
    font-size: 16px;
    border-radius: 14px;
    background: #c5cdd4;
    box-shadow: inset 19px 19px 38px #a9b0b6, inset -19px -19px 38px #e1eaf2;
    margin-bottom: 25px;
    &:focus {
      outline: none;
    }
  }
</style>

<input class="text-field" type="text" bind:value={bindedValue} />
