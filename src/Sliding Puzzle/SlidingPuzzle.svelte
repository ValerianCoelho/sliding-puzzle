<script>
  // @ts-ignore
  import { onMount } from "svelte";
  import Piece from "./Piece.svelte";

  export let rows;
  export let cols;
  export let src;
  export let width;
  export let gap;

  let imgWidth;
  let imgHeight;
  let physicalImgWidth;
  let physicalImgHeight;
  let puzzlePieceWidth;
  let puzzlePieceHeight;
  let pieceTranslationCoords = [];
  let bgImgCoords = [];
  let coords = [];
  $:freeSpace = { x: cols - 1, y: rows - 1, src}; // src is only added here as a dependency
  
  function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
  }

 // @ts-ignore
   $: {
    console.log("Reacted")
    const image = new Image();
    image.src = src;

    image.onload = () => {
      imgWidth = width;
      imgHeight = (width * image.height) / image.width;
      physicalImgWidth = parseFloat(imgWidth) + (cols - 1) * gap;
      // @ts-ignore
      physicalImgHeight = parseFloat(imgHeight) + (rows - 1) * gap;
      puzzlePieceWidth = imgWidth / cols;
      puzzlePieceHeight = imgHeight / rows;
    };

    pieceTranslationCoords = [];
    bgImgCoords = [];
    for (let i = 0; i < rows; i++) {
      let coord = [];
      for (let j = 0; j < cols; j++) {
        if (i == rows - 1 && j == cols - 1) {
          break;
        }
        coord.push({ x: j, y: i });
      }
      pieceTranslationCoords.push(coord);
      const tempCoord = [...coord];
      shuffleArray(tempCoord);
      bgImgCoords.push(tempCoord);
    }
    coords = []
  }
  $:{
    if(coords.length == 0) {
      coords = pieceTranslationCoords.map((value, RowIndex) => {
      return value.map((subvalue, ColIndex) => {
        return { translation: subvalue, background: bgImgCoords[RowIndex][ColIndex] };
      });
    });
    }
  }

</script>

<div class="sliding-puzzle-container" style={`width: ${physicalImgWidth}px; height: ${physicalImgHeight}px;`}>
  {#each coords as value}
    {#each value as subvalue}
      <Piece
        translation={subvalue.translation}
        position={subvalue.background}
        gap={gap}
        imgSrc={src}
        imgWidth={imgWidth}
        imgHeight={imgHeight}
        puzzlePieceWidth={puzzlePieceWidth}
        puzzlePieceHeight={puzzlePieceHeight}
        on:click={() => {
          console.log("clicked")
          let coord = subvalue.translation;
          let x = Math.abs(freeSpace.x - coord.x);
          let y = Math.abs(freeSpace.y - coord.y);
          if (x + y <= 1) {
            [subvalue.translation, freeSpace] = [freeSpace, subvalue.translation];
          }
        }}
      />
    {/each}
  {/each}
</div>

<style>
  .sliding-puzzle-container {
    position: relative;
  }
</style>
