<script>
  import Counter from './Counter.svelte'

  export let name

  let query = ''
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
</script>

<style>
  h1 {
    color: purple;
  }

  input {
    display: block;
  }

  .search {
    width: 250px;
  }

  ul {
    list-style: none;
    max-height: 250px;
    overflow-y: auto;
  }

  ul > li {
    padding: 0.5rem 0;
  }

  article {
    display: none;
  }

  article.active {
    display: block;
  }
</style>

<h1>Hello {name}!</h1>
<Counter />

<h2>You are querying "{query}"</h2>
<section class="search">
  <input
    class="search input"
    type="text"
    bind:value={query}
    placeholder="search text" />
  <article class:active={query} class="search suggestions">
    <ul>
      {#each suggestions.filter(s => query && s.startsWith(query)) as suggestion (suggestion)}
        <li>{suggestion}</li>
      {/each}
    </ul>
  </article>
</section>
