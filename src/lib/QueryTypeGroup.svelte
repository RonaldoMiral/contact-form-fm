<script>
  import Label from "./Label.svelte";
  import RadioFiled from "./RadioField.svelte";

  let selectedValue = "";
</script>

<div class="radios-container">
  <Label label="Query Type" />
  <RadioFiled
    id="enquiry_radio"
    value="General Enquiry"
    bind:group={selectedValue}
  />

  <RadioFiled
    value="Support Request"
    id="request_radio"
    bind:group={selectedValue}
  />
  <p class="error_message">Please select a type query</p>
</div>

<style>
  .radios-container {
    display: grid;
    gap: 1.6rem;
  }

  .error_message {
    color: var(--pr-red);
  }
</style>
