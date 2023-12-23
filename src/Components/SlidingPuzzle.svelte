<script>
  import { onMount } from "svelte";

  export let rows;
  export let cols;
  export let src;

  let imgWidth;
  let imgHeight;

  let puzzlePieceWidth;
  let puzzlePieceHeight;

  const rowIndices = Array.from({length: rows}, (_, index) => index);
  const colIndices = Array.from({length: cols}, (_, index) => index);

  const coords = [];

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
      for(let j=0; j<cols; j++) {
        coords.push({x: i, y: j})
      }
    }
    console.log(coords)
  })

  function convertCoordToIndex(i, j) {
    return i * cols + j;
  }

</script>

<div class="sliding-puzzle-container">
  {#each rowIndices as i}
    {#each colIndices as j}
      <div 
        class="puzzle-piece" 
        style={` 
            transform: translate(${puzzlePieceWidth * j + (j * 2)}px, ${puzzlePieceHeight * i + (i * 2)}px);
            width: ${puzzlePieceWidth}px;
            height: ${puzzlePieceHeight}px;
            background-image: url(${src});
            background-size: ${imgWidth}px, ${imgHeight}px;
            // we are trying to access the coords values before they are initialized, so its throwing an error
            background-position: -${puzzlePieceWidth * coords[convertCoordToIndex(i, j)].x}px -${puzzlePieceHeight * coords[convertCoordToIndex(i, j)].y}px; 
        `}
      >
        Hello
      </div>
    {/each}
  {/each}
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
