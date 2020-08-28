<script>
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();

    export let name;
    export let day;

    let showControls = false;

    const addDay = () => (day += 1);
    const removeDay = () => (day -= 1);
    const toggleControls = () => (showControls = !showControls);
</script>

<style>
    .card {
        position: relative;
    }

    .card-content {
        padding-left: 3em;

    }

    .card-content-name {
        font-size: larger;
        font-weight: bold;
        color: #204f6e;
    }

    .card-content-days {}

    .card-expand {
        position: absolute;
        top: 1.1em;
        left: 1em;
        background: none;
        border: none;
        padding: 0;
        outline: none;
        width: 2em;
    }

    .card-actions {
        padding-left: 3em;
        margin-top: 1em;
    }

    .card-actions-button {
        padding: 0.25em 0.5em
    }

    .card-actions-delete-button {
        padding: 0.4px 8px;
        background: #dc3545;
        color: azure;
        position: absolute;
        top: 1em;
        right: 1em;
        border: none;
        outline: none;
    }
    .card-actions-input {}

</style>

<article class="card">
    <div class="card-content">
        <div class="card-content-name">{name}</div>
        <div class="card-content-days">Days: {day}</div>
    </div>

    <button class="card-expand" on:click={toggleControls}>
        {#if showControls}-{:else}+{/if}
    </button>
    <button class="card-actions-delete-button" on:click={() => dispatch('removeperson', name)}>x</button>

    {#if showControls}
        <div class="card-actions">
            <input class="card-actions-input" type="number" bind:value={day}>
            <button class="card-actions-button" on:click={addDay}>+1</button>
            <button class="card-actions-button" on:click={removeDay}>-1</button>
        </div>
    {/if}
</article>