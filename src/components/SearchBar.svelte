<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let selected = "";

  const handleChange = () => {
    dispatch("filter", selected);
  };
</script>

<div class="search-bar">
  <label for="rating">Filter by Rating:</label>
  <select bind:value={selected} on:change={handleChange}>
    <option value="">All</option>
    {#each Array(10) as _, i}
      <option value={10 - i}>{10 - i}</option>
    {/each}
  </select>
</div>

<style> 
  .search-bar {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 20px 0;
  }

  select {
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 16px;
  }
</style>
