<script>
  export let movies;
</script>

<h2>List of movies</h2>

{#if movies.lenght > 0}
  <ul>
    {#each movies as movie (movie.id)}
      <li>
        {movie.title}
        |
        {movie.year}
        |
        <a href={movie.url}>Movie link</a>
      </li>
    {/each}
  </ul>
{:else}
	<p><b>No data</b></p>
{/if}

