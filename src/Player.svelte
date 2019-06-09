  <script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

  export let name;
  export let points;
  const addPoints = () => points += 1;
  const removePoints = () => points -= 1;
  let showControlls = false;
  const toggleControll = () => (showControlls = !showControlls);
  const removePlayer = () => {
      dispatch('removeplayer', name);
  }
</script>

<style>
  h1 {
    color: purple;
  }
  .mt-n1 {
  margin-bottom: 10px;
}
.card_{
/* width: 18rem; */
padding: 10px;
margin: 10px 0;

}
</style>


<div class="card card_">
    <h1>{name}
	<button class="btn" on:click={toggleControll}>
	{#if showControlls}-{:else}+{/if}
	</button>
	<button class="btn btn-danger btn-sm" on:click={removePlayer}>&times;</button>
	</h1>
    <h3>{points}</h3>
	{#if showControlls}
	<div class="mt-n1">
	<button class="btn" on:click={addPoints}>+1</button>
	<button class="btn btn-dark" on:click={removePoints}>-1</button>
	</div>
	<input type="number" bind:value={points} />
	{/if}
  </div>