<script>
  import Output from "../Output/index.svelte";

  import checkedIcon from "../../../assets/icons/checked.png";

  export let label;
  export let checked;
</script>

<style lang="scss">
  .checkbox {
    flex: 1;
    display: flex;
    align-items: center;

    &__input {
      position: absolute !important;
      height: 1px;
      width: 1px;
      overflow: hidden;
      clip: rect(1px 1px 1px 1px); /* IE6, IE7 */
      clip: rect(1px, 1px, 1px, 1px);
      white-space: nowrap; /* added line */
    }
    &__icon {
      position: relative;
      flex-basis: 30px;
      flex-shrink: 0;

      width: 30px;
      height: 30px;
      display: flex;
      justify-content: center;
      align-items: center;
      &:before {
        position: absolute;
        content: "";
        width: 30px;
        height: 30px;
        left: 0px;
        top: 0px;
        border: 2px solid grey;
        border-radius: 3px;
        box-sizing: border-box;
      }
      img,
      svg {
        max-width: 75%;
        position: relative;
        z-index: 2;
      }
    }
    span {
      font-size: 16px;
      font-weight: 600;
      text-overflow: ellipsis;
      max-width: 100%;
      min-height: 30px;
      box-sizing: border-box;
      &.checked{
        text-decoration: line-through;
      }
    }
  }
</style>

<label class="checkbox">
  <input class="checkbox__input" type="checkbox" bind:checked />
  <Output>
    <div class="checkbox__icon">
      {#if checked}
        <img src={checkedIcon} alt="" />
      {/if}
    </div>
  </Output>
  <Output fullWidth={true}>
    {#if label}
      <span class:checked>{label}</span>
    {/if}
  </Output>

</label>
