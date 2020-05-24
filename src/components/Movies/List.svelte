<script>
  import Card from './../ui/card.svelte'
  export let movies = [];
  export let movie_count = 0;

  // $: if (movie_count && movie_count > 0) {
  //   alert(`count is dangerously high!`);
  // }
  console.log({movie_count, movies})

</script>

<h2>List of movies</h2>

<div class="row">
  {#if movie_count > 0 || movies.lenght > 0}
    {#each movies as movie (movie.id)}
      <Card movie={movie}/>
    {/each}
  {:else}
    <p>No movies found</p>
  {/if}
</div>

<style>

  /* Remove extra left and right margins, due to padding */
  .row {margin: 0 -5px;}

  /* Clear floats after the columns */
  .row:after {
    content: "";
    display: table;
    clear: both;
  }

</style>

