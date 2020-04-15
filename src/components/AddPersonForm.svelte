<script>
  import { createEventDispatcher } from 'svelte'

  let dispatch = createEventDispatcher()

  let name
  let beltColor
  let age
  let skills = []

  const handleSubmit = () => {
    const person = { name, beltColor, age, skills, id: Math.random() }
    dispatch('addPerson', person)
  }
</script>

<h3>Add a new person</h3>

<form on:submit|preventDefault={handleSubmit} >
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age}/>

  <label for="skill">Skills</label>
  <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
  <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
  <input type="checkbox" bind:group={skills} value="running">running<br>

  <label for="belt-color">Belt color</label>
  <select name="belt-color" id="belt-color" bind:value={beltColor}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>

  <button>Add person</button>
</form>

<style>

</style>
