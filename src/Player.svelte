<script>
  import Navbar from "./Navbar.svelte";

  export let name;
  export let points;

  const addOne = () => (points += 1);
  const subtractOne = () => (points -= 1);
  let showControls = false;
  const toggleControls = () => (showControls = !showControls);
</script>

<main>
  <h1>Hello {name}!</h1>
  <button on:click={toggleControls}>
    {#if showControls} Hide controls {:else}Show controls{/if}
  </button>
  <p>You have {points} points.</p>
  {#if showControls}
    <button on:click={addOne}>Add point</button>
    <button on:click={subtractOne}>Subtract point</button>
    <input type="number" name="" id="" bind:value={points} />
  {/if}
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
