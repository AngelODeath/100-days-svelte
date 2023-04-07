<!-- DiaryEntry.svelte -->
<li>
    <div class="entry-thumbnail">
      <img src="{thumbnail}" alt="{title} thumbnail">
    </div>
    <div class="entry-summary">
      <h3>{title}</h3>
      <p>{summary}</p>
      <a href="#">Read more</a>
    </div>
  </li>
  
  <script>
    export let thumbnail;
    export let title;
    export let summary;
  </script>
  
  <style>
    /* CSS styles for the component */
    /* ... */
  </style>
  