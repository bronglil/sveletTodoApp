<script>
  import { createEventDispatcher } from "svelte";
  import Card from "./Card.svelte";
  export let item;
  const dispatch = createEventDispatcher();
  const handleDelete = ({ id }) => {
    dispatch("delete-feedback", id);
  };
</script>

<Card>
  <div class="num-display">{item.rating}</div>
  <button class="close" on:click={() => handleDelete({ id: item?.id })}
    >X</button
  >
  <div class="text_display">{item?.text}</div>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background-color: #ff6a95;
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
