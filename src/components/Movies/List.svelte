<script>
  export let movies;

  $: if (movies.lenght > 0) {
    alert(`count is dangerously high!`);
  }

</script>

<h2>List of movies</h2>

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

