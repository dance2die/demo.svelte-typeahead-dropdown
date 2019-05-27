<script>
  export let count = 0
</script>

<style>
  .counter-container {
    display: flex;
    flex-direction: column;
  }
</style>

<section class="counter-container">
  <h2>Count {count}</h2>
  <article>
    <button on:click={() => count++}>+</button>
    <button on:click={() => count--}>-</button>
  </article>
</section>
