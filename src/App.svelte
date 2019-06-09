<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    { name: "Aviral", points: 100 },
    { name: "Ashu", points: 80 },
    { name: "Abhishek", points: 60 },
    { name: "Rinku", points: 90 },
    { name: "Raju", points: 20 }
  ];
const addPlayerNew = (e) => {
	const newPlayer = e.detail;
	players = [...players, newPlayer];
}
const removePlayer = e => {
	players = players.filter(player => player.name !== e.detail);
}
</script>

<Navbar />
<div class="container " style=" padding: 10px;">
  <AddPlayer on:addplayer={addPlayerNew} />

  {#if players.length === 0}
    <p>No Players available!!</p>
  {:else}
    {#each players as player}
      <Player name={player.name} points={player.points} on:removeplayer={removePlayer} />
    {/each}
  {/if}

</div>
