<script>
  import FeedbackItem from "./FeedbackItem.svelte";

  export let feedback = [];
</script>

<main>
  {#each feedback as fb (fb.id)}
    <FeedbackItem item={fb} on:delete-feedback />
  {/each}
</main>

<style>
</style>
