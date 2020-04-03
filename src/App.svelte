<script>
  let firstName = "Jimmy"
  let lastName = "Hendrix"
  let beltColor = "black"
  let people = [
    { name: "Yoshi", beltColor: "black", age: 25, id: 1},
    { name: "Mario", beltColor: "orange", age: 35, id: 2},
    { name: "Luigi", beltColor: "brown", age: 45, id: 3},
  ]

  $: fullName = `${firstName} ${lastName}`

  $: {
    console.log(fullName)
  }

  const handleClick = (id) => {
    people = people.filter(p => p.id !== id)
  }

  const handleInput = (e) => {
    beltColor = e.target.value
  }
</script>

<main>
  <p>{fullName} - {beltColor} belt</p>
  <input type="text" bind:value={firstName}>
  <input type="text" bind:value={lastName}>
  <input type="text" bind:value={beltColor}>

  {#each people as p (p.id)}
    <div>
      <h4>{p.name}</h4>
      <p>{p.age} - {p.beltColor}</p>
      <button on:click={() => handleClick(p.id)}>Delete</button>
    </div>
  {:else}
    <p>No people to show.</p>
  {/each}
</main>

<style type="text/scss">
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
