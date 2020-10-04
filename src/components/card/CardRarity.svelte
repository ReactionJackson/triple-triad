<script>
  export let stars

  const starRotations = [ 0, 1, 4, 2, 3 ]
  const getRotateStyle = rotation => `rotate(${ rotation * (360 / starRotations.length) }deg)`

</script>

<div class="stars">
  {#each starRotations as rotation, star}
    {#if stars >= star}
      <div
        class="star-arm"
        style="transform: { getRotateStyle(rotation)  }">
        <div
          class="star"
          style="transform: translate3d(-50%, -50%, 0) { getRotateStyle(-rotation) } scale3d(1, -1, 1)">
        </div>
      </div>
    {/if}
  {/each}
</div>

<style>
  .stars {
    position: absolute;
    left: 9%;
    top: 6%;
    width: 30px;
    height: 30px;
    transform: scaleY(-1);
  }
  .stars .star-arm {
    position: absolute;
    left: 50%;
    top: 50%;
    width: 0;
    height: 10px;
    transform-origin: center top;
  }
  .stars .star-arm .star {
    content: '★';
    position: absolute;
    left: 50%;
    top: 100%;
    width: 10px;
    height: 10px;
    background: url('../assets/img/star.png') center no-repeat;
  }
</style>
