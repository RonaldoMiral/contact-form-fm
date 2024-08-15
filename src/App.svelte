<script>
  import TextField from "./lib/TextField.svelte";
  import MessageField from "./lib/MessageField.svelte";
  import ConsentCheck from "./lib/ConsentCheck.svelte";
	import RadioField from "./lib/RadioField.svelte";
  import Label from "./lib/Label.svelte";
  import MessageSent from "./lib/MessageSent.svelte";

	// USER INFO
	let name = '';
	let lastName = '';
	let emailAddress = '';

	let selectedRadioValue = '';
	let message = '';
	let consented = false;
	let sent = false;

	// ERROR STATES
	let nameFieldIsNotEmpty = false,
	lastNameFieldIsNotEmpty = false,
	emailAddressFieldIsNotEmpty = false,
	queryTypeSelected = false,
	messageIsNotEmpty = false,
	consentChecked = false;

	function sendForm() {
		!name ? nameFieldIsNotEmpty = true : nameFieldIsNotEmpty = false;
		!lastName ? lastNameFieldIsNotEmpty = true : lastNameFieldIsNotEmpty = false;
		!emailAddress ? emailAddressFieldIsNotEmpty = true : emailAddressFieldIsNotEmpty = false;
		!selectedRadioValue ? queryTypeSelected = true : queryTypeSelected = false;
		!message ? messageIsNotEmpty = true : messageIsNotEmpty = false;
		!consented ? consentChecked = true : consentChecked = false;

		if(
			nameFieldIsNotEmpty || lastNameFieldIsNotEmpty ||
			emailAddressFieldIsNotEmpty || queryTypeSelected ||
			messageIsNotEmpty || consentChecked
		) return;

		const userInfo = {
			name, lastName, emailAddress,
			queryType: selectedRadioValue,
			message, consent: consented
		}

		const key = name.concat(lastName);
		const userInfoJson = JSON.stringify(userInfo);
		
		name = '';
		lastName = '';
		emailAddress = '';
		selectedRadioValue = '';
		message = '';
		consented = false;
		sent = true;
		localStorage.setItem(key, userInfoJson);
		setTimeout(() => sent = false, 3000);
	}

</script>

<main>
	<MessageSent {sent} />
	<form>
    <h1>Contact Us</h1>
    <div class="container">
			<TextField
				inputType='text'
				error={nameFieldIsNotEmpty}
				label='Name'
				bind:value={name}
			/>
			<TextField
				inputType='text'
				error={lastNameFieldIsNotEmpty}
				label='Last Name'
				bind:value={lastName}
			/>
			<TextField
				inputType='email'
				error={emailAddressFieldIsNotEmpty}
				label='Email Address'
				bind:value={emailAddress}
			/>

      <!-- <QueryTypeGroup /> -->
			<div class="radios-container">
				<Label label="Query Type" />
				<div class="radios">
					<RadioField
						id="enquiry_radio"
						value="General Enquiry"
						bind:group={selectedRadioValue}
					/>
				
					<RadioField
						value="Support Request"
						id="request_radio"
						bind:group={selectedRadioValue}
					/>
				</div>
				<p class="error_message {queryTypeSelected ? 'error' : ''}">Please select a type query</p>
			</div>

      <MessageField bind:value={message} error={messageIsNotEmpty} />
    </div>
    <ConsentCheck bind:checked={consented} error={consentChecked} />
    <button type="submit" on:click|preventDefault={sendForm}>Submit</button>
  </form>
</main>

<style>
  main {
    min-width: 32rem;
    /* max-width: 37.5rem; */
    padding: 3.2rem 1.6rem;
    margin: auto;
		height: 100vh;
		position: relative;
		display: grid;
		align-items: center;
  }

  form {
    background-color: var(--ntl-white);
    padding: 2.4rem;
    display: grid;
    gap: 3.2rem;
    border-radius: 1.6rem;
  }

  .container {
    display: grid;
    row-gap: 2.4rem;
  }

  /* Radio Incorporation */
  .radios-container, .radios {
    display: grid;
    gap: 1.6rem;
  }

	.radios-container .error_message {
		display: none;
	}

	.radios-container .error_message.error {
		display: block;
		color: var(--pr-red);
	}

  button {
    height: 5.9rem;
    cursor: pointer;
    border-radius: 0.8rem;
    border: 0;
    background-color: var(--pr-green-600);
    color: var(--ntl-white);
    font-weight: var(--ft-w-700);
  }

  @media (min-width: 768px) {
    main {
      width: 69rem;
      max-width: 69rem;
    }

    .container {
      grid-template-columns: repeat(2, 1fr);
      column-gap: 1.6rem;
    }

		.radios-container {
			grid-column: span 2;
		}

		.radios {
			grid-template-columns: repeat(2, 1fr);
		}
  }
</style>