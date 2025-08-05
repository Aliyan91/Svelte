<script>
    import Feedbackitem from "./Feedbackitem.svelte";
    export let feedback = [];

    console.log(feedback)
</script>


{#each feedback as fb (fb.id)}
    <Feedbackitem item={fb} on:delete-feedback/>
{/each}