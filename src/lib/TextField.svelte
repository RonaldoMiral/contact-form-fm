<script>
  import Label from "./Label.svelte";

  export let inputType;
  export let label;
  export let value;
  export let error;
</script>

<div class="field-container">
  <Label {label} />
    {#if inputType === 'text'}
      <input type="text" name="" class:error bind:value id={label} />
    {:else if inputType === 'email'}
      <input type="email" name="" class:error bind:value id={label} />
    {/if}
  <p class="error_message {error ? "error" : ""}">This field is required</p>
</div>

<style>
  input {
    height: 5.1rem;
    border-radius: 0.8rem;
    outline: 0;
    border: 1px solid var(--ntl-grey-500);
    padding: 1.2rem 2.4rem;
  }

  input:hover {
    cursor: pointer;
    border-color: var(--pr-green-600);
  }

  input:focus {
    outline: 1px solid var(--pr-green-600);
    border: 0;
  }

  @media (min-width: 768px) {
    .field-container:has(input[type="email"]) {
        grid-column: span 2;
    }
  }

  .error {
    border-color: var(--pr-red);
  }

  .error_message {
    display: none;
  }

  .error_message.error {
    display: block;
    color: var(--pr-red);
  }
</style>
