<script>
  import { Feedbackstore } from "../store";
  import Feedbackitem from "./Feedbackitem.svelte";
  import { fade, scale } from "svelte/transition";
  let feedback = [];

  Feedbackstore.subscribe((data) => (feedback = data));
</script>

{#each feedback as fb (fb.id)}
  <div in:scale out:fade={{ duration: 500 }}>
    <Feedbackitem item={fb}  />
  </div>
{/each}
