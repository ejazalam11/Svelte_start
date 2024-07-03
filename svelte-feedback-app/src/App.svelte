<script>
  let Firstname = "Ejaz";
  let LastName = "alam";
  let color = "blue";
  let showText = false;
  //   $: name = ""
  const toggle = () => {
    color = color === "blue" ? "green" : "blue";
    showText = !showText;
  };

  let users = [
    {
      id: "1",
      name: "Ejaz",
    },
    {
      id: "2",
      name: "Asad",
    },
    {
      id: "3",
      name: "Ali",
    },
  ];
</script>

<main>
  <h1 style="color:{color}">Hello {Firstname} {LastName}!</h1>
  {#if showText}
    <p>
      Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
      how to build Svelte apps.
    </p>
  {:else}
    <p>No Text untill you click the button</p>
  {/if}

  <button on:click={toggle}>Click</button>

  {#each users as user (user.id)}
    <h3>{user.id}:{user.name}</h3>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
