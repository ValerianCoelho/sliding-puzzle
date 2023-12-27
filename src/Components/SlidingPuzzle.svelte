<script>
  import { onMount } from "svelte";
  import Piece from "./Piece.svelte";

  export let rows;
  export let cols;
  export let src;

  let imgWidth;
  let imgHeight;

  let puzzlePieceWidth;
  let puzzlePieceHeight;

  const rowIndices = Array.from({length: rows}, (_, index) => index);
  const colIndices = Array.from({length: cols}, (_, index) => index);

  $:pieceTranslationCoords = []; // this will not be randomized, it will change as the user plays
  $:bgImgCoords = []; // this will be randomized only once at the begining and after that it wont change

  onMount(()=> {
    const image = new Image();
    image.src = src;

    image.onload = () => {
      imgWidth = 400;
      imgHeight = (400 * image.height) / image.width;

      puzzlePieceWidth = imgWidth / cols;
      puzzlePieceHeight = imgHeight / rows;
    };

    for(let i=0; i<rows; i++) {
      let coord = []
      for(let j=0; j<cols; j++) {
        coord.push({x: j, y: i})
      }
      pieceTranslationCoords.push(coord);
      bgImgCoords.push(coord);
    }
    console.log(pieceTranslationCoords)
    console.log(bgImgCoords)
  })

</script>

<div class="sliding-puzzle-container">
  {#if pieceTranslationCoords.length > 0}
    {#each rowIndices as i}
      {#each colIndices as j}
        <Piece
          x={j}
          y={i}
          
          imgSrc={src}
          imgWidth={imgWidth}
          imgHeight={imgHeight}

          puzzlePieceWidth={puzzlePieceWidth}
          puzzlePieceHeight={puzzlePieceHeight}

        />
      {/each}
    {/each}
  {/if}
</div>

<style>
  .sliding-puzzle-container {
    position: relative;
  }
  .puzzle-piece {
    position: absolute;
    background-color: red;
    color: white;
  }
</style>
