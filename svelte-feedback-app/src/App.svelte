<script>
  import Feedbacklist from "./components/Feedbacklist.svelte";
  import FeedbackStates from "./components/FeedbackStates.svelte";
  import FeedbackForm from "./components/FeedbackForm.svelte";
  let feedback = [
    {
      id: 1,
      rating: 10,
      text: " In publishing and graphic design, Lorem ipsum is a placeholder text commonly used to demonstrate the visual form of a document or a typeface without relying on meaningful content.",
    },
    {
      id: 2,
      rating: 8,
      text: " In publishing and graphic design, Lorem ipsum is a placeholder text commonly used to demonstrate the visual form of a document or a typeface without relying on meaningful content.",
    },
    {
      id: 3,
      rating: 9,
      text: " In publishing and graphic design, Lorem ipsum is a placeholder text commonly used to demonstrate the visual form of a document or a typeface without relying on meaningful content.",
    },
  ];

  $: count = feedback.length;
  $: average =
    feedback.reduce((a, { rating }) => a + rating, 0) / feedback.length;

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((item) => item.id != itemId);
  };
</script>

<main class="container">
  <FeedbackForm />
  <FeedbackStates {count} {average} />
  <!-- {average} -->
  <Feedbacklist {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
