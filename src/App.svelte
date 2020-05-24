<script>
  import axios from 'axios';
  import MoviesList from './components/Movies/List.svelte'
  import MoviesSearch from './components/Movies/Search.svelte'

  let search = '';
  let query  = '';
  let year   = '';
  let getMovies = getAllMovies();

  async function getAllMovies() {
    try {
      const url = `https://yts.mx/api/v2/list_movies.json?${query}`;
      const res = await axios(url);

      if (res.data) {
        return res.data.data;
      }

      return []
    } catch (error) {
      console.error('Error: ', error)
    }
  }

  function addParams() {
    query = 'query_term=' + search;
    if (year !== '') {
      query += ` ${year}`;
    }
  }

  function handleSubmit(){
    addParams();

    getMovies = getAllMovies();
    console.log('query: ', query);
  }

</script>

<h1>Search movies wrapper - App</h1>

<MoviesSearch bind:input={search} bind:year={year} on:submit={handleSubmit}/>

{#await getMovies}
  <p>...waiting</p>
{:then data}
  <MoviesList
    movies={data.movies}
    movie_count={data.movie_count}
  />
{:catch error}
  <p style="color: red">{error.message}</p>
{/await}
