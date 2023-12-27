<script>
  export let translation;
  export let position;

  export let imgSrc;
  export let imgWidth;
  export let imgHeight;

  export let puzzlePieceWidth;
  export let puzzlePieceHeight;

  $:Translation = `translate(${puzzlePieceWidth * translation.x + (translation.x * 2)}px, ${puzzlePieceHeight * translation.y + (translation.y * 2)}px)`
  $:Position = `-${puzzlePieceWidth * position.x}px -${puzzlePieceHeight * position.y}px`;

</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click
  class="puzzle-piece" 
  style={` 
      transform: ${Translation};
      background-image: url(${imgSrc});
      background-position: ${Position}; 
      background-size: ${imgWidth}px, ${imgHeight}px;
      width: ${puzzlePieceWidth}px;
      height: ${puzzlePieceHeight}px;
  `}
>
  {translation.x}, {translation.y}
</div>

<style>
  .puzzle-piece {
    position: absolute;
    background-color: red;
    color: white;
  }
</style>
