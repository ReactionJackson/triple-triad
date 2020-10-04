<script>
  export let stats = { numeric: { top: 0, right: 0, bottom: 0, left: 0 } }

  const { top, right, bottom, left } = stats.numeric
  const getStatStyle = stat => `background-position: left ${ (stat - 1) * -15 }px center;`

</script>

<div class="stats">
  <div class="stat" style="{ getStatStyle(left) }"></div>
  <div>
    <div class="stat" style="{ getStatStyle(top) }"></div>
    <div class="stat" style="{ getStatStyle(bottom) }"></div>
  </div>
  <div class="stat" style="{ getStatStyle(right) }"></div>
</div>

<style>
  .stats {
    z-index: 100;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    pointer-events: none;
    width: 45px;
    height: 30px;
    margin-bottom: 15px;
    transform: scale(1.1);
  }
  .stats .stat {
    color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 15px;
    height: 15px;
    margin: -1px 0;
    background: url('../../assets/img/numbers.png') left center no-repeat;
  }
</style>
