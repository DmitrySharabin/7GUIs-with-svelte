<!-- https://eugenkiss.github.io/7guis/tasks#counter -->
<script>
  let counter = 0;
</script>

<main>
  <input readonly value={counter} />
  <button on:click={() => counter += 1}>Count</button>
</main>
