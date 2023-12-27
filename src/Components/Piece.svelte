<script>
  export let translation;
  export let position;

  export let imgSrc;
  export let imgWidth;
  export let imgHeight;

  export let puzzlePieceWidth;
  export let puzzlePieceHeight;

  function calculateBgPosition() {
    const backgroundPosition = `-${puzzlePieceWidth * position.x}px -${puzzlePieceHeight * position.y}px`;
    return backgroundPosition;
  }

  function calculatePieceTranslation() {
    const pieceTranslation = `translate(${puzzlePieceWidth * translation.x + (translation.x * 2)}px, ${puzzlePieceHeight * translation.y + (translation.y * 2)}px)`
    return pieceTranslation;
  }

</script>

<div 
  class="puzzle-piece" 
  style={` 
      transform: ${calculatePieceTranslation()};
      background-image: url(${imgSrc});
      background-position: ${calculateBgPosition()}; 
      background-size: ${imgWidth}px, ${imgHeight}px;
      width: ${puzzlePieceWidth}px;
      height: ${puzzlePieceHeight}px;
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
