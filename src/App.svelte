<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    { name: "John Doe", points: 22 },
    { name: "Jane Doe", points: 12 },
    { name: "John Titor", points: 15 },
  ];

  const addPlayer = (e) => {
    const newPlayerData = e.detail;
    // States are immutable so you can't push it
    players = [...players, newPlayerData];
  };

  const removePlayer = (e) => {
    players = players.filter((player) => player.name !== e.detail);
  };
</script>

<main>
  <Navbar />
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <p>No players</p>
  {:else}
    {#each players as player}
      <Player name={player.name} points={player.points} on:removeplayer={removePlayer} />
    {/each}
  {/if}
</main>

<style>
</style>
