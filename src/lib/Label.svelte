<script>
    export let label;
</script>

<label for={label}>{label}<span>*</span></label>

<style>
    label {
        color: var(--ntl-grey-900);
    }

    span {
        margin-left: .8rem;
        color: var(--pr-green-600);
    }
</style>