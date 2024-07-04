<script>
  import Feedbacklist from "./components/Feedbacklist.svelte";

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

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((item) => item.id != itemId);
  };
</script>

<main class="container">
  <Feedbacklist {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
