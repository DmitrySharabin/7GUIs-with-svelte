<!-- https://eugenkiss.github.io/7guis/tasks#flight -->
<script>
	let flight;
	let departureDate = getISODate(new Date());
	let returnDate = getISODate(new Date());

	$: canBook = flight === "one way" || Date.parse(returnDate) > Date.parse(departureDate);

	const showConfirmation = () => {
		const message =
			flight === "return"
				? `You have booked a return flight leaving on ${departureDate} and returning on ${returnDate}.`
				: `You have booked a one-way flight leaving on ${departureDate}.`;

		alert(message);
	};

	function getISODate(date) {
		return date.toISOString().split("T")[0];
	}
</script>

<main>
	<select bind:value={flight}>
		<option value="one way">One-way Flight</option>
		<option value="return">Return Flight</option>
	</select>

	<input type="date" bind:value={departureDate} />

	<input type="date" bind:value={returnDate} disabled={flight !== "return"} />

	<button disabled={!canBook} on:click={showConfirmation}>Book</button>

	{#if !canBook}
		<p>⚠️ Return date must be after departure date!</p>
	{/if}
</main>

<style>
	main {
		display: grid;
		grid-template-columns: min-content;
		gap: 0.3em;
	}
</style>
