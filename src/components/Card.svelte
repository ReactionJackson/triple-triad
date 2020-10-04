<script>
  import { PLAYERS, ART_OFFSETS, SPEEDS } from '../constants'
  import CardStats from './card/CardStats.svelte'
  import CardRarity from './card/CardRarity.svelte'

  export let owner = PLAYERS.P1
  export let card = {}

  const { id, image, stars, stats } = card

  let isFlipping = false

  const switchOwnership = () => {
    isFlipping = true
    setTimeout(() => {
      owner = owner === PLAYERS.P1 ? PLAYERS.P2 : PLAYERS.P1
      setTimeout(() => isFlipping = false, SPEEDS.FLIP / 2)
    }, SPEEDS.FLIP / 2)
  }

  const getArtwork = (id, offset) => `https://github.com/mattantonelli/ffxiv-triple-triad-data/raw/master/images/0${ offset + id }.png`

</script>

<div class="card">
  <div class="inner { isFlipping ? 'disabled' : '' }" class:isFlipping on:click="{ switchOwnership }">
    <div class="card-back"></div>
    <div class="card-color { owner === PLAYERS.P1 ? 'blue' : 'red' }"></div>
    <div class="card-artwork" style="background-image: url({ getArtwork(id, ART_OFFSETS.CARD) })"></div>
    <CardRarity { stars } />
    <CardStats { stats } />
  </div>
</div>

<style>

  @keyframes flipCard {
    0% { transform: scale(1) rotateY(0deg); }
    50% { transform: scale(1.3) rotateY(180deg); }
    100% { transform: scale(1) rotateY(360deg); }
  }

  .card {
    position: relative;
    transition: transform ease 100ms;
    perspective: 400px;
  }
  .card:hover {
    z-index: 8888;
    transform: scale(1.1);
  }
  .card .inner {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: flex-end;
    width: 120px;
    height: 150px;
    cursor: pointer;
    user-select: none;
    transform-style: preserve-3d;
  }
  .disabled {
    pointer-events: none;
  }
  .card .inner.isFlipping {
    z-index: 9999;
    animation: flipCard linear 450ms forwards;
  }
  .card-artwork {
    position: absolute;
    width: 100%;
    height: 100%;
    background-size: cover;
    backface-visibility: hidden;
  }
  .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    background: url('../assets/img/card-back.png') center no-repeat;
    background-size: cover;
    transform: rotateY(180deg) translateZ(1px);
    backface-visibility: hidden;
  }
  .card-color {
    position: absolute;
    width: 100%;
    height: 100%;
    transform: scale3d(0.85, 0.9, 1);
    backface-visibility: hidden;
  }
  .card-color.blue {
    background-color: #3f5e7c;
  }
  .card-color.red {
    background-color: #a53537;
  }
</style>
