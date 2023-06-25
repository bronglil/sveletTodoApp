<script>
  import FeedBackForm from "./component/FeedBackForm.svelte";
  import FeedbackList from "./component/FeedbackList.svelte";
  import FeedbackStats from "./component/FeedbackStats.svelte";

  let feedbacks = [
    {
      id: 1,
      rating: 7,
      text: "Lorem Ipsum is simply dummy text of the printing and typesetting industry.  Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
    },
    {
      id: 2,
      rating: 10,
      text: "Lorem Ipsum is simply dummy text of the printing and typesetting industry.  Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
    },
    {
      id: 3,
      rating: 5,
      text: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
    },
  ];

  $: count = feedbacks.length;
  $: average =
    feedbacks.reduce((a, { rating }) => a + rating, 0) / feedbacks.length;

  const deleteFeedback = (e) => {
    feedbacks = feedbacks.filter((feedback) => feedback.id !== e?.detail);
  };

  const handleAddFeedback = (e) => {
    const { id, rating, text } = e?.detail;

    const isDuplicate = feedbacks.some(
      (item) => item.id === id && item.rating === rating && item.text === text
    );
    if (isDuplicate) {
      alert("Duplicate id or rating found");
      return;
    }
    feedbacks = [...feedbacks, e?.detail];
  };
</script>

<main class="container">
  <FeedBackForm on:add-feedback={handleAddFeedback} />
  <FeedbackStats {count} {average} />
  <FeedbackList {feedbacks} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
