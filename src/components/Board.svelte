<script>
  import Card from './Card.svelte'

  export let decks = [[], []]

  $: console.log('decks', decks)

</script>

<div class="main-board">
  {#each [...Array(9)] as _, i }
    <div class="space"></div>
  {/each}
</div>

<style>
  .main-board {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
    width: 490px;
    height: 490px;
    padding: 10px;
    background-color: #e5e3d8;
  }
  .main-board .space {
    display: flex;
    justify-content: center;
    background-color: rgba(0, 0, 0, 0.05);
  }
</style>
