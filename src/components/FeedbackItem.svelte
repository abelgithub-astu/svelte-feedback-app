<script>
  import Card from "./Card.svelte";
  import { feedbackStore } from "../store";
  export let item;

  const handleDelete = (itemid) => {
    feedbackStore.update((currentFeedback) => {
      return currentFeedback.filter((item) => item.id !== itemid);
    });
  };
</script>

<Card>
  <div class="num-display">
    {item.rating}
  </div>
  <button on:click={() => handleDelete(item.id)} class="close">X</button>
  <p class="text-display">{item.text}</p>
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
