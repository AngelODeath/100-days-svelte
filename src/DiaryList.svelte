<!-- DiaryList.svelte -->
<script>
    import DiaryEntry from './DiaryEntry.svelte';
  
    export let entries;
  </script>
  
  <ul>
    {#each entries as entry}
      <DiaryEntry
        thumbnail={entry.thumbnail}
        title={entry.title}
        summary={entry.summary}
      />
    {/each}
  </ul>
  
  <style>
    /* CSS styles for the component */
    /* ... */
  </style>
  