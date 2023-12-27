<script>
  export let x;
  export let y;

  export let imgSrc;
  export let imgWidth;
  export let imgHeight;

  export let puzzlePieceWidth;
  export let puzzlePieceHeight;

  function calculateBgPosition(x, y) {
    const backgroundPosition = `-${puzzlePieceWidth * x}px -${puzzlePieceHeight * y}px`;
    return backgroundPosition;
  }

  function calculatePieceTranslation(x, y) {
    const pieceTranslation = `translate(${puzzlePieceWidth * x + (x * 2)}px, ${puzzlePieceHeight * y + (y * 2)}px)`
    return pieceTranslation;
  }

</script>

<div 
  class="puzzle-piece" 
  style={` 
      transform: ${calculatePieceTranslation(x, y)};
      background-image: url(${imgSrc});
      background-position: ${calculateBgPosition(x, y)}; 
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
