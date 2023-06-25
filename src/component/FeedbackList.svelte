<script>
  import FeedbackItem from "./FeedbackItem.svelte";
  export let feedbacks = [];
</script>

<main>
  {#each feedbacks as fb (fb?.id)}
    <FeedbackItem item={fb} on:delete-feedback />
  {/each}
</main>
