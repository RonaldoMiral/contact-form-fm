<script>
    export let value;
    export let group;
    export let id;

    $: active = group === value;
</script>


<label for={id} class="container" class:active>
    <input
        type="radio"
        {id}
        {value}
        bind:group
    >
    <p>{ value }</p>
</label>


<style>
    .container {
        border: 1px solid var(--ntl-grey-500);
        height: 5.1rem;
        border-radius: .8rem;
        padding: 1.2rem 2.4rem;
        cursor: pointer;

        display: flex;
        align-items: center;
        gap: 1.2rem;
    }

    .container:hover {
        border-color: var(--pr-green-600);
    }

    .container.active {
        background-color: var(--pr-green-200);
        border-color: var(--pr-green-600);
    }

    .container::before {
        content: "";
        width: 2rem;
        height: 2rem;
        box-shadow: 0 0 0 1px var(--ntl-grey-500);
        border-radius: 50%;
    }
    
    .container.active::before {
        box-shadow: none;
        background-image: url('/assets/icon-radio-selected.svg');
        background-repeat: no-repeat;
    }

    input[type="radio"] {
        display: none;        
    }

</style>