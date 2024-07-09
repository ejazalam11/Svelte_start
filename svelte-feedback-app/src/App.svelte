<script>
  import { onMount } from "svelte";
  let posts = [];
  //   import { Router, Link, Route } from "svelte-routing";

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
  onMount(async () => {
    const data = await fetch("https://jsonplaceholder.typicode.com/posts");
    posts = await data.json();
  });
  let submit = false;
  let countt = 2;

  const Clickbtn = () => {
    countt++;
  };

  $: if (countt === 3) {
    alert("You have reached number 2");
  }
</script>

<main class="container">
  <button on:click={Clickbtn} class="btn"
    >{countt}{countt <= 1 ? "time" : "times"}</button
  >

  <FeedbackForm />
  <FeedbackStates {count} {average} />
  {average}
  <Feedbacklist {feedback} on:delete-feedback={deleteFeedback} />
  {#each posts as post (post.id)}
    <h3>{post.id} - {post.title}</h3>
  {/each}

  <label>
    <input type="checkbox" bind:checked={submit} />
    I have Read the arguments!
    <button type="submit" disabled={!submit}> Submit</button>
  </label>
</main>

<style>
  h3 {
    color: rgb(35, 33, 33);
  }

  .btn {
    padding: 9px;
  }
</style>
