<script>
  import { createEventDispatcher } from "svelte";

  export let name;
  export let points;

  const dispatch = createEventDispatcher();

  const addOne = () => (points += 1);
  const subtractOne = () => (points -= 1);
  let showControls = false;
  const toggleControls = () => (showControls = !showControls);
  const onDelete = () => dispatch("removeplayer", name);
</script>

<main>
  <h1>{name} has {points} points!</h1>
  <button on:click={toggleControls}>
    {#if showControls} Hide controls {:else}Show controls{/if}
  </button>
  {#if showControls}
    <button on:click={onDelete}>Delete</button>
    <button on:click={addOne}>Add point</button>
    <button on:click={subtractOne}>Subtract point</button>
    <input type="number" name="" id="" bind:value={points} />
  {/if}
  <hr />
</main>

<style>
</style>
