<script>
  import axios from 'axios';
  import MoviesList from './components/Movies/List.svelte'
  import MoviesSearch from './components/Movies/Search.svelte'

  let search = '';
  let query  = '';
  let year   = '';
  let data   = getAllMovies();

  async function getAllMovies() {
    try {
      const url = `https://yts.mx/api/v2/list_movies.json?${query}`;
      const res = await axios(url);
      console.log(res)
      if (res.data) {
        console.log('data: ', res.data.data)
        return res.data.data;
      }

      return []
    } catch (error) {
      console.log('Error: ', error)
    }
  }

  function showInput(){
    query = 'query_term=' + search;
    if (year !== '') {
      query += ` ${year}`;
    }

    data = getAllMovies()
    console.log('Search: ', search)
  }

</script>

<h1>Search movies wrapper - App</h1>

<MoviesSearch bind:input={search} bind:year={year} on:submit={showInput}/>

{#await data}
  <p>...waiting</p>
{:then data}
  <MoviesList movies={data.movies}/>
{:catch error}
  <p style="color: red">{error.message}</p>
{/await}
