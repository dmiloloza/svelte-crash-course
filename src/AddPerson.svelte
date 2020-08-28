<script>
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();

    let person = {
        name: '',
        day: null
    };
    const onSubmit = e => {
        dispatch('addperson', person)
        person = {
            name: '',
            day: null
        }
    };
</script>

<form class="grid-3" on:submit|preventDefault={onSubmit}>
    <input bind:value={person.name} placeholder="Person name" type="text">
    <input bind:value={person.day} placeholder="days" type="date">
    <input class="btn btn-primary" type="submit" value="Add Person" disabled={!person.name, !person.day}>
</form>