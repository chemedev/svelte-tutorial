<script>
  let firstName = 'Jimi';
  let lastName = 'Hendrix';
  let beltColour = 'black';

  $: fullName = `${firstName} ${lastName}`;
  $: {
    console.log(beltColour);
    console.log(fullName);
  }

  const handleClick = () => {
    beltColour = 'orange';
  };
  const handleInput = e => {
    beltColour = e.target.value;
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

<main>
  <p style="color: {beltColour}">{fullName} - {beltColour} belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="text" bind:value={beltColour} />
</main>
