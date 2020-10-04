<script>
  import Card from './Card.svelte'

  export let deck
  export let player
  export let username

</script>

<div class="player-board">
  <div class="deck">
    {#each deck as card}
      <div class="space">
        <Card owner={ player } { card } />
      </div>
    {/each}
  </div>
</div>

<style>
  .player-board {
    display: flex;
    align-items: flex-end;
    background-color: #7e5a8e;
  }
  .deck {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: flex-start;
    width: 450px;
    padding: 5px 0;
  }
  .deck .space {
    display: flex;
    justify-content: center;
    width: 120px;
    height: 150px;
    margin: 5px;
    background-color: rgba(0, 0, 0, 0.1);
    border-radius: 20px;
  }
</style>
