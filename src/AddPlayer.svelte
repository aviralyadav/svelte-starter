<script>
import { createEventDispatcher } from "svelte"; 
const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 0
  };
  const onSubmit = (e) => {
      e.preventDefault();
      dispatch("addplayer", player);
      player = {
          name: "",
          points: 0
      }
  };
</script>

<form on:submit={onSubmit}>
  <div class="form-group">
    <input
      type="text"
      bind:value={player.name}
      class="form-control"
      placeholder="Player Name" />
  </div>
  <div class="form-group">
    <input
      type="number"
      class="form-control"
      bind:value={player.points}
      placeholder="Player Points" />
  </div>
  <button type="submit" class="btn btn-primary">Add Player</button>
</form>
