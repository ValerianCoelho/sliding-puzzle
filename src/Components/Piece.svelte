<script>
  export let translate;
  export let puzzlePieceWidth;
  export let puzzlePieceHeight;
  export let imgSrc;
  export let imgWidth;
  export let imgHeight;
  export let backgroundPosition;
</script>

<div 
  class="puzzle-piece" 
  style={` 
      transform: ${translate};
      width: ${puzzlePieceWidth}px;
      height: ${puzzlePieceHeight}px;
      background-image: url(${imgSrc});
      background-size: ${imgWidth}px, ${imgHeight}px;
      background-position: ${backgroundPosition}; 
  `}
>
  
</div>

<style>
  .puzzle-piece {
    position: absolute;
    background-color: red;
    color: white;
  }
</style>
