<script>
  export let style = "primary";
  export let type = "button";
  export let disabled = false;
</script>

<button {type} {disabled} class={style}>
  <slot />
</button>

<style>
  button {
    color: white;
    border: 0;
    border-radius: 8px;
    width: 100px;
  }

  .primary {
    background-color: #202142;
  }
  .secondary {
    background-color: #ff6a95;
  }

  button:hover {
    transform: scale(0.98);
    opacity: 0.9;
  }

  button:disabled {
    background-color: #cccccc;
    color: #333;
    cursor: auto;
  }
</style>
