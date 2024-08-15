<script>
  export let error;
  export let checked;
</script>

<div class="consent-container">
  <input type="checkbox" name="" id="consent" bind:checked={checked} />
  <label for="consent">
    <p>I consent to being contacted by the team<span>*</span></p>
  </label>
  <p class="error_message" class:error>To submit this form, please consent to being contacted</p>
</div>

<style>
  .consent-container {
    margin: 1.6rem 0;
    width: fit-content;
    padding: 0 .1rem;
  }

  label {
    cursor: pointer;
    display: grid;
    grid-template-columns: 1.8rem 1fr;
    gap: 1.6rem;
    align-items: center;
    padding-right: .7rem;
  }

  label::before {
    box-sizing: border-box;
    content: '';
    width: 1.8rem;
    height: 1.8rem;
    border: 1px solid var(--ntl-grey-500);
  }

  label span {
    margin-left: 0.8rem;
    color: var(--pr-green-600);
  }

  input {
    display: none;
  }

  input:checked + label::before {
    background-image: url("/assets/icon-checkbox-check.svg");
    background-repeat: no-repeat;
    background-size: 1.8rem 1.8rem;
    height: 1.8rem;
    border: 0;
  }

  .error_message {
    margin-top: .8rem;
    color: var(--pr-red);
    display: none;
  }

  .error_message.error {
    display: block;
  }
</style>
