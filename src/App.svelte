<script>
    import Navbar from './Navbar.svelte';
    import Person from './Person.svelte';
    import AddPerson from './AddPerson.svelte';

    let people = [
        {
            name: 'Pepi',
            day: 7
        },
        {
            name: 'Nita',
            day: 7
        },
        {
            name: 'Jole',
            day: 4
        },
        {
            name: 'Marac',
            day: 3
        }
    ];

    const addPerson = e => {
        const newPerson = e.detail;
        people = [...people, newPerson]
    };

    const removePerson = e => {
        people = people.filter(person => person.name !== e.detail);
    };
</script>

<Navbar/>

<div class="container">
    <AddPerson on:addperson={addPerson}/>
    {#if people.length === 0}
        <p align="center"><b>No cases</b></p>
        <hr>
        <p align="center">Everyone is perfectly healthy!</p>
    {:else}
        {#each people as person}
            <Person name={person.name} day={person.day}
                    on:removeperson={removePerson}/>
        {/each}
    {/if}
</div>


