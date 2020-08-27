<script>
    let name = 'John Doe';
    let points = 100;
    let showControls = false;

    const addPoint = () => (points += 1);
    const removePoint = () => (points -= 1);
    const toggleControls = () => (showControls = !showControls);

</script>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    h1 {
        color: #204f6e;
        text-transform: uppercase;
        font-size: 2em;
        font-weight: 100;
    }

    h3 {
        margin-bottom: 10px;
    }


</style>

<div class="container">
    <div class="card">
        <main>
            <h1>
                {name}
                <button class="btn btn-sm" on:click={toggleControls}>+</button>
            </h1>
            <h3>{points}</h3>
            {#if showControls}
                <button class="btn" on:click={addPoint}>+1</button>
                <button class="btn btn-dark" on:click={removePoint}>-1</button>
                <input type="number" bind:value={points}>
            {/if}
        </main>
    </div>
</div>


