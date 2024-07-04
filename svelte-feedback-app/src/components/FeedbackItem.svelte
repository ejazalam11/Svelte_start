<script>
  import { createEventDispacher } from "svelte";
  import Cart from "./Cart.svelte";
  export let item;

  const dispatch = createEventDispacher();
  const handleDelete = (itemId) => {
    dispatch("delete-feedback", itemId);
  };
</script>

<Cart>
  <div class="num-display">
    {item.rating}
  </div>
  <button class="close" on:click={() => handleDelete(item.id)}>X</button>
  <div class="text-display">
    {item.text}
  </div>
</Cart>

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
    /* margin-left: 10px; */
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
