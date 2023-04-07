<script>
  export let entries;

  // Compute the average mood score for the past 100 days
  function getAverageMood(entries) {
    const numEntries = Math.min(entries.length, 100);
    let totalMood = 0;
    for (let i = 0; i < numEntries; i++) {
      totalMood += entries[i].mood;
    }
    return totalMood / numEntries;
  }

  // Compute the most common tag for the past 100 days
  function getMostCommonTag(entries) {
    const numEntries = Math.min(entries.length, 100);
    const tagCounts = {};
    for (let i = 0; i < numEntries; i++) {
      const tags = entries[i].tags
        ? entries[i].tags.split(",").map((tag) => tag.trim())
        : [];
      for (const tag of tags) {
        if (tag in tagCounts) {
          tagCounts[tag]++;
        } else {
          tagCounts[tag] = 1;
        }
      }
    }
    let maxCount = 0;
    let mostCommonTag = "";
    for (const tag in tagCounts) {
      if (tagCounts[tag] > maxCount) {
        maxCount = tagCounts[tag];
        mostCommonTag = tag;
      }
    }
    return mostCommonTag;
  }
</script>

<section class="summary">
  <h2>Summary</h2>
  <p>Average Mood: {getAverageMood(entries).toFixed(2)}</p>
  <p>Most Common Tag: {getMostCommonTag(entries)}</p>
</section>

<style>
  /* CSS styles for the component */
  /* ... */
</style>
