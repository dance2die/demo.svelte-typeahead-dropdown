<script>
  export let count = 0
</script>

<h1>Count {count}</h1>

<button on:click={() => count++}>+</button>
<button on:click={() => count--}>-</button>
