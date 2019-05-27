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
</style>

<h1>Hello {name}!</h1>
<Counter />

<h2>You are querying "{query}"</h2>
<section class="search">
  <input type="text" bind:value={query} placeholder="search text" />
  <article class="suggestions">
    <ul>
      {#each suggestions.filter(s =>
        s.startsWith(query)
      ) as suggestion (suggestion)}
        <li>{suggestion}</li>
      {/each}
    </ul>
  </article>
</section>
