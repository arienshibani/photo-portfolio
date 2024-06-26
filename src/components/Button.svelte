<script>
export let text = "";
export let isDisabled = false;
export let onClick = () => {};
</script>

  <style>
    .button {
      display: inline-block;
      padding: 0.5em 1em;
      border: 2px solid black;
      background-color: black;
      color: white;
      font-size: 1em;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s ease, color 0.3s ease;
    }

    .button:hover {
      background-color: white;
      color: black;
    }

    .button:active {
      background-color: gray;
    }

    .button:focus {
      outline: none;
      box-shadow: 0 0 0 3px gray;
    }

    .button:disabled {
      background-color: gray;
      border-color: gray;
      color: white;
      cursor: not-allowed;
    }
  </style>

  <button
    class="button"
    on:click={onClick}
    disabled={isDisabled}
  >
    {text}
  </button>
