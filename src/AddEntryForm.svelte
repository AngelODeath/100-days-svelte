<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let title = "";
  let text = "";
  let mood = 5;
  let tags = "";

  // Function to handle form submission
  function handleSubmit(event) {
    event.preventDefault();
    const newEntry = {
      title,
      text,
      mood: Number(mood),
      tags,
    };
    dispatch("add-entry", newEntry);
    title = "";
    text = "";
    mood = 5;
    tags = "";
  }

  // Function to handle cancel button click
  function handleCancel() {
    dispatch("cancel-click");
    title = "";
    text = "";
    mood = 5;
    tags = "";
  }
</script>

<section class="add-entry-form">
  <h2>Add New Entry</h2>
  <form on:submit={handleSubmit}>
    <label>
      Title:
      <input type="text" bind:value={title} required />
    </label>
    <label>
      Text:
      <textarea bind:value={text} required />
    </label>
    <label>
      Mood:
      <select bind:value={mood}>
        <option value="1">1 (Terrible)</option>
        <option value="2">2 (Bad)</option>
        <option value="3">3 (Okay)</option>
        <option value="4">4 (Good)</option>
        <option value="5">5 (Great)</option>
      </select>
    </label>
    <label>
      Tags:
      <input type="text" bind:value={tags} />
    </label>
    <div class="button-group">
      <button type="submit">Add Entry</button>
      <button type="button" on:click={handleCancel}>Cancel</button>
    </div>
  </form>
</section>

<style>
  .add-entry-form {
    margin: 2rem 0;
    padding: 1rem;
    background-color: #f5f5f5;
    border: 1px solid #ddd;
    border-radius: 4px;
  }

  .add-entry-form h2 {
    margin-top: 0;
    margin-bottom: 1rem;
  }

  .add-entry-form form label {
    display: block;
    margin-bottom: 0.5rem;
  }

  .add-entry-form form input,
  .add-entry-form form textarea,
  .add-entry-form form select {
    display: block;
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 1rem;
  }

  .add-entry-form .button-group {
    display: flex;
    justify-content: flex-end;
    margin-top: 1rem;
  }

  .add-entry-form .button-group button {
    margin-left: 1rem;
    background-color: #6c63ff;
    color: white;
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
  }
  .add-entry-form .button-group button:hover {
    background-color: #5245cc;
  }
</style>
