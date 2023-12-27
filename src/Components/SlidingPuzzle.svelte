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

  let freeSpace = {x: cols-1, y: rows-1};

  const rowIndices = Array.from({length: rows}, (_, index) => index);
  const colIndices = Array.from({length: cols}, (_, index) => index);

  $:pieceTranslationCoords = []; // this will not be randomized, it will change as the user plays
  $:bgImgCoords = []; // this will be randomized only once at the begining and after that it wont change

  function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
  }

  onMount(()=> {
    const image = new Image();
    image.src = src;

    image.onload = () => {
      imgWidth = 400;
      imgHeight = (400 * image.height) / image.width;

      puzzlePieceWidth = imgWidth / cols;
      puzzlePieceHeight = imgHeight / rows;
    };

    for (let i = 0; i < rows; i++) {
      let coord = [];
      for (let j = 0; j < cols; j++) {
        if (i == rows - 1 && j == cols - 1) {
          break;
        }
        coord.push({ x: j, y: i });
      }
      pieceTranslationCoords.push(coord);
      const tempCoord = [...coord]
      shuffleArray(tempCoord);
      bgImgCoords.push(tempCoord);
    }
  })

</script>

<div class="sliding-puzzle-container">
  {#if pieceTranslationCoords.length > 0}
    {#each rowIndices as i}
      {#each colIndices as j}
        {#if i!=rows-1 || j!=cols-1}
          <Piece
            translation={pieceTranslationCoords[i][j]}
            position={bgImgCoords[i][j]}
            
            imgSrc={src}
            imgWidth={imgWidth}
            imgHeight={imgHeight}

            puzzlePieceWidth={puzzlePieceWidth}
            puzzlePieceHeight={puzzlePieceHeight}

            on:click={()=>{
              [pieceTranslationCoords[i][j], freeSpace] = [freeSpace, pieceTranslationCoords[i][j]]
            }}
          />
        {/if}
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
  .test {
    z-index: 3;
    color: red;
  }
</style>
