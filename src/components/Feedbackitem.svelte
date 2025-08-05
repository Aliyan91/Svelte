<script>
  import { Feedbackstore } from "../store";
  import Card from "./Card.svelte";
  export let item;

  const handledelete = (itemId) => {
    Feedbackstore.update((currentFeedback) => {
      return currentFeedback.filter((item) => item.id != itemId);
    });
  };
</script>

<Card>
  <div class="num-display">
    {item.rating}
  </div>
  <button class="close" on:click={() => handledelete(item.id)}>x</button>
  <div class="text-display">
    {item.text}
  </div>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background: #ff6a95;
    color: #fff;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }

  .close {
    position: absolute;
    top: 10px;
    right: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>
