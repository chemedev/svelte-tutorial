<script>
  import Modal from './Modal.svelte';
  import AddPersonForm from './AddPersonForm.svelte';

  let showModal = false;

  const toggleModal = () => {
    showModal = !showModal;
  };

  let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1, skills: [] },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2, skills: [] },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3, skills: [] }
  ];

  const handleClick = (e, id) => {
    people = people.filter(person => person.id !== id);
  };

  const addPerson = e => {
    console.log(e.detail);
    const person = e.detail;
    people = [person, ...people];
    showModal = false;
  };
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<Modal {showModal} on:click={toggleModal}>
  <AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
  <button on:click|once={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === 'black'}
        <p>
          <strong>MASTER NINJA</strong>
        </p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt</p>
      {#each person.skills as skill, i}
        <p>{skill}</p>
      {/each}
      <button on:click={e => handleClick(e, person.id)}>delete</button>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>
