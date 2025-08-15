<script>
  import { Feedbackstore } from "./store";
  import Feedbackliist from "./components/Feedbackliist.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";
  import Feedbackform from "./components/Feedbackform.svelte";
  import { onDestroy, onMount } from "svelte";
  import SeacrhBar from "./components/SearchBar.svelte";

  let eedback = [];

  let filterRatings="";
  const handleFilter = (e) => {
    filterRatings = e.detail; 
  };

  const unsubscribe = Feedbackstore.subscribe((data) => (feedback = data));

  onDestroy(() => {
    unsubscribe();
  });
  onMount(() => {
    console.log("hello");
  });

  

  $: count = feedback.length;
  $: average =
    feedback.reduce((a, { rating }) => a + rating, 0) / feedback.length;

  const addFeedback = (e) => {
    const newFeedback = e.detail;
    feedback = [newFeedback, ...feedback];
  };
</script>

<main class="container">
  <SeacrhBar on:filter={handleFilter}></SeacrhBar>
  <Feedbackform on:add-feedback={addFeedback}></Feedbackform>
  <FeedbackStats {count} {average} />
  <Feedbackliist {filterRatings} />
</main>

<style>
</style>
