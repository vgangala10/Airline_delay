<script>
	import { onMount } from 'svelte';
	import Sunburst from './Sunburst.svelte';
	import * as d3 from 'd3';
  
	let data; // This will hold the fetched data
	  
	onMount(async () => {
	  try {
		// Replace 'result_data_final.json' with the correct path to your JSON data
		data = await d3.json('result_data_final.json');
	  } catch (error) {
		console.error('Failed to load data:', error);
	  }
	});
  </script>
  
  <svelte:head>
	<title>Federal Aviation Details in USA</title>
	<link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
  </svelte:head>
  
  <header class="navbar navbar-expand-lg navbar-dark custom-navbar">
	<a class="navbar-brand" href="#">Airline On-Time Statistics & Delay Causes</a>
  </header>
  
  <div class="container-fluid h-100">
	<div class="row h-100">
	  <div class="col-md-6 d-flex align-items-center">
		<div>
		  <!-- Place your text content here -->
		  <h3>Airline On-Time Statistics & Delay Causes</h3>
		  <p style="text-align: justify;">A zoomable sunburst is a data visualization technique that represents hierarchical data in a circular form, where each ring of the sunburst represents a level of the hierarchy. Users can interactively zoom in and out of the sunburst to explore deeper levels of the hierarchy and gain insights into the relationships between data elements.</p>

          <p style="text-align: justify;">Employing a zoomable sunburst visualization implemented in D3, our graphical representation offers a comprehensive exploration of online airlines, delay causes, and statistical insights across various dimensions such as airline, year, and month. This interactive tool enables users to seamlessly zoom in and out, delving deeper into the intricate hierarchy of flight data, gaining a nuanced understanding of performance patterns over time. The percentage-based presentation of flight statistics enhances clarity, allowing users to discern on-time performance metrics effortlessly.</p>

		  <p style="text-align: justify;">Derived from data provided by the Federal Aviation Administration, our visualization encapsulates high-level flight details, including critical insights into the on-time statistics of each airline. This integration of comprehensive data from a reputable source empowers users to make informed interpretations and comparisons, fostering a deeper comprehension of the aviation landscape. The interactive and user-friendly nature of our zoomable sunburst visualization not only enhances accessibility but also transforms complex aviation data into an engaging and insightful experience..</p>
		

		  <!-- Add more text content as needed -->
		</div>
	  </div>
	  <div class="col-md-6 d-flex align-items-center justify-content-center">
		{#if data}
		  <Sunburst {data} />
		{:else}
		  <p>Loading...</p>
		{/if}
	  </div>
	</div>
  </div>
  
  <style>
	.custom-navbar {
	  background: linear-gradient(
		to right, 
		rgba(0, 0, 0, 1) 0%, 
		rgba(0, 0, 0, 1) 70%, /* Black base */
		rgba(255, 255, 255, 0.15) 85%, /* Shiny highlight towards the right */
		rgba(0, 0, 0, 1) 100%
	  ); /* Creates a shiny effect moving from left to right */
	  color: #fff;
	  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5); /* Soften the lower edge */
	  border-bottom: 1px solid rgba(255, 255, 255, 0.3); /* Subtle bottom highlight */
	}
  
	.container-fluid {
	  padding-top: 56px; /* Adjust if necessary */
	}
	
	.row.h-100 {
	  min-height: calc(100vh - 56px); /* Adjusted for navbar height */
	  margin-top: -20px; /* Reduce or adjust the top margin */
	}
  
	.col-md-6:first-child div {
	  margin-right: 20px; /* Spacing between text and chart, adjust if necessary */
	}
  
	.col-md-6:last-child > div {
	  margin-top: -50px; /* Adjust this value as needed to move Sunburst up */
	}
  </style>
  