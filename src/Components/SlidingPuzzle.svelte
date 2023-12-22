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
        coords.push({x: j, y: i})
      }
    }
    console.log(coords)
  })

</script>

<div class="sliding-puzzle-container">
  {#each coords as coord}
    <div 
      class="puzzle-piece" 
      style={` 
          transform: translate(${puzzlePieceWidth * coord.x + (coord.x * 2)}px, ${puzzlePieceHeight * coord.y + (coord.y * 2)}px);
          width: ${puzzlePieceWidth}px;
          height: ${puzzlePieceHeight}px;
          background-image: url(${src});
          background-size: ${imgWidth}px, ${imgHeight}px;
          background-position: -${puzzlePieceWidth * coord.x}px -${puzzlePieceHeight * coord.y}px; 
      `}
    >
      Hello
    </div>
  {/each}
</div>

<style>
  .sliding-puzzle-container {
    position: relative;
  }
  .puzzle-piece {
    position: absolute;
    background-color: red;
  }
</style>
