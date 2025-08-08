<script>
  import { Feedbackstore } from "../store";
  import Feedbackitem from "./Feedbackitem.svelte";
  import { fade, scale } from "svelte/transition";
  let feedback = [];
  export let filterRatings = "";


  Feedbackstore.subscribe((data) => (feedback = data));

   $: filteredFeedback = filterRatings
    ? feedback.filter((item) => item.rating == filterRatings)
    : feedback;
</script>

{#if filteredFeedback.length > 0}
  {#each filteredFeedback as fb (fb.id)}
    <div in:scale out:fade={{ duration: 500 }}>
      <Feedbackitem item={fb} />
    </div>
  {/each} 
{:else}
  <p>No feedback found for this rating.</p>
{/if}