<script>
	import { onMount } from 'svelte';
	import Sunburst from '/home/runner/work/airlines.github.io/src/routes/Sunburst.svelte';
	import * as d3 from 'd3';

	let data; // This will hold the fetched data

	onMount(async () => {
		try {
			// Replace 'result_data_final.json' with the correct path to your JSON data
			data = await d3.json('./../data/result_data_final.json');
			//console.log(data); // Logging the fetched data to console
		} catch (error) {
			console.error('Failed to load data:', error);
		}
	});
</script>

<main>
	{#if data}
	    <h1>Airline Delay details</h1>
		<Sunburst {data} />
	{:else}
		<p>Loading...</p>
	{/if}
</main>

<style>
	main {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}
</style>
