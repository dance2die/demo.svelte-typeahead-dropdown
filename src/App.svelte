<script>
  import Counter from './Counter.svelte'

  let name

  let query = ''
  let selectedQuery = undefined

  let suggestions = [
    'calendar-dates',
    'dangerous',
    'dangerous-components',
    'styled-components',
    'abc',
    'abbc',
    'abbbbc',
    'hel',
    'hell',
    'hello',
    'help',
    'helping',
  ]

  function handleSearchButton(e) {
    if (query) {
      query = ''
    }
  }

  function handleItemClick(e, suggestion) {
    e.preventDefault()
    query = suggestion
    selectedQuery = query
  }
</script>

<style>
  h1 {
    color: purple;
  }

  ul {
    list-style: none;
    max-height: 250px;
    overflow-y: auto;

    /* https://y34o5l3p61.codesandbox.io/ */
    transition: opacity 0.1s ease;
    border-radius: 0 0 0.28571429rem 0.28571429rem;
    box-shadow: 0 2px 3px 0 rgba(34, 36, 38, 0.15);
    border-color: #9b4dca;
    border-top-width: 0px;
    border-right-width: 1px;
    border-bottom-width: 1px;
    border-left-width: 1px;
    border-style: solid;
  }

  li {
    margin: 0;
    padding: 0.6rem 0.5rem;
  }

  li:hover {
    background: rgba(0, 0, 0, 0.13);
    color: black;
    cursor: pointer;
  }

  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .search {
    width: 250px;
  }

  .search.suggestions {
    display: none;
  }

  .search.container {
    position: relative;
  }

  .search.input.active {
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
  }

  .search input {
    margin: 0;
  }

  .search button {
    position: absolute;
    top: 0;
    right: 0;

    border: none;
    background-color: transparent;
    color: black;

    margin: 0 -2rem;
  }

  .search.suggestions.active {
    display: block;
  }

  hr {
    width: 50vw;
  }
</style>

<section class="container">

  <h1>Hello {name}!</h1>
  <Counter />

  <hr />

  <h2>You are querying "{query}"</h2>
  <section class="search">
    <article class="search container">
      <input
        class="search input"
        class:active={query}
        type="text"
        bind:value={query}
        on:input={() => (selectedQuery = '')}
        placeholder="search text" />
      <button on:click={handleSearchButton}>{query && '❌'}</button>
    </article>
    <article class:active={!selectedQuery && query} class="search suggestions">
      <ul>
        {#each suggestions.filter(s => query && s.startsWith(query)) as suggestion (suggestion)}
          <li on:click={e => handleItemClick(e, suggestion)}>{suggestion}</li>
        {/each}
      </ul>
    </article>
  </section>

</section>
