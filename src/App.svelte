<!-- https://eugenkiss.github.io/7guis/tasks#temp -->
<script>
  let c, f;

  function toFahrenheit () {
    f = c * (9/5) + 32;
  }

  function toCelsius () {
    c = (f - 32) * (5/9)
  }
</script>

<main>
  <input type="number" bind:value={c} on:input={toFahrenheit} /> Celsius =
  <input type="number" bind:value={f} on:input={toCelsius} /> Fahrenheit
</main>
