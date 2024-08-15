<script>
  import Label from "./Label.svelte";


  export let value;
  export let error;
  let focused = false;
</script>

<div class="field-container">
    <Label label='Message' />
    <div class="message-container" class:error class:focused>
        <textarea name="" id="message-field"
            on:focus={ () => focused = true }
            on:blur={ () => focused = false }
            bind:value
        ></textarea>
    </div>
    <p class="error_message" class:error>This field is required</p>
</div>


<style>
    .message-container {
        border: 1px solid var(--ntl-grey-500);
        height: 24.3rem;
        border-radius: .8rem;
        padding: 1.2rem 2.4rem;
    }
    
    .message-container.focused {
        border: 0;
        outline: 1px solid var(--pr-green-600);
    }
    
    textarea {
        border: 0;
        width: 100%;
        height: 100%;
        resize: none;
        outline: 0;
        overflow: hidden;
        padding: 0;
        line-height: 1.5;
    }

    @media (min-width: 768px) {
        .field-container {
            grid-column: span 2;
        }

        .message-container {
            height: 13.2rem;
        }
    }

    
    .message-container.error {
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


