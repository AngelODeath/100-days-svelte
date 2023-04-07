<script>
	import { onMount, createEventDispatcher } from 'svelte';
	import DiaryList from './DiaryList.svelte';
	import Summary from './Summary.svelte';
	import AddEntryForm from './AddEntryForm.svelte';
  
	let entries = [];
	let showForm = false;
  
	const dispatch = createEventDispatcher();
  
	function handleAddEntry(event) {
	  showForm = true;
	}
  
	function handleCancel() {
	  showForm = false;
	}
  
	function handleAddEntrySubmit(event) {
	  entries = [event.detail, ...entries.slice(0, 99)];
	  showForm = false;
	}
  
	function handleCancelClick() {
	  showForm = false;
	}
  
	function getMostCommonTag(entries) {
	  const numEntries = Math.min(entries.length, 100);
	  const tagCounts = {};
	  for (let i = 0; i < numEntries; i++) {
		const tags = entries[i].tags.split(',').map(tag => tag.trim());
		for (const tag of tags) {
		  if (tag in tagCounts) {
			tagCounts[tag]++;
		  } else {
			tagCounts[tag] = 1;
		  }
		}
	  }
	  let maxCount = 0;
	  let mostCommonTag = '';
	  for (const tag in tagCounts) {
		if (tagCounts[tag] > maxCount) {
		  maxCount = tagCounts[tag];
		  mostCommonTag = tag;
		}
	  }
	  return mostCommonTag;
	}
  
	let mostCommonTag = '';
	$: {
	  mostCommonTag = getMostCommonTag(entries);
	}
  </script>

<main class="container">
	<header class="header">
	  <h1>100 Days Diary</h1>
	  <button on:click={handleAddEntry}>Add Entry</button>
	</header>
  
	{#if showForm}
	  <AddEntryForm on:add-entry={handleAddEntrySubmit} on:cancel-click={handleCancelClick} />
	{:else}
	  <div class="entry-list">
		<DiaryList entries={entries} />
	  </div>
  
	  <div class="summary">
		<h2>Summary</h2>
		<p>Most common tag: {mostCommonTag}</p>
		<Summary entries={entries} />
	  </div>
	{/if}
  </main>

<style>
	body {
		background-color: #f9f9f9;
		font-family: sans-serif;
	}

	.container {
		max-width: 800px;
		margin: 0 auto;
		padding: 2rem;
	}

	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 2rem;
	}

	.header h1 {
		margin: 0;
		font-size: 2.5rem;
	}

	.header button {
		background-color: #6c63ff;
		color: white;
		padding: 0.5rem 1rem;
		border: none;
		border-radius: 4px;
		font-size: 1rem;
		cursor: pointer;
	}

	.header button:hover {
		background-color: #5245cc;
	}

	.entry-list {
		margin-top: 2rem;
	}

	.entry {
		background-color: white;
		border: 1px solid #ddd;
		border-radius: 4px;
		padding: 1rem;
		margin-bottom: 1rem;
	}

	.entry h2 {
		margin-top: 0;
		margin-bottom: 0.5rem;
	}

	.entry p {
		margin-top: 0;
		margin-bottom: 1rem;
	}

	.entry .tags {
		display: flex;
		flex-wrap: wrap;
		margin-top: 0.5rem;
	}

	.entry .tag {
		background-color: #eee;
		color: #333;
		border-radius: 4px;
		padding: 0.25rem 0.5rem;
		margin-right: 0.5rem;
		margin-bottom: 0.5rem;
		font-size: 0.875rem;
	}

	.summary {
		margin-top: 2rem;
		background-color: white;
		border: 1px solid #ddd;
		border-radius: 4px;
		padding: 1rem;
	}

	.summary h2 {
		margin-top: 0;
		margin-bottom: 0.5rem;
	}

	.summary p {
		margin-top: 0;
		margin-bottom: 0.5rem;
	}
</style>
