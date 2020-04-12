<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let input = '';
  export let year  = '';

  const years = [
    '2020', '2018', '2010', '2005'
  ]

  const submit = () => dispatch('submit');
</script>

<div>
  <input bind:value={input} placeholder="enter your movie title">
  <select bind:value={year}>
  {#each years as y}
    <option value={y}>
      {y}
    </option>
  {/each}
</select>
  <button on:click={submit}>search!</button>
</div>
