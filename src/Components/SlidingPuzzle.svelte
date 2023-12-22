<script>
  import { onMount } from "svelte";

  export let rows;
  export let cols;
  export let src;

  let imgWidth;
  let imgHeight;

  let puzzlePieceWidth;
  let puzzlePieceHeight;

  const rowIndices = Array.from({length: 5}, (_, index) => index + 1);
  const colIndices = Array.from({length: 5}, (_, index) => index + 1);

  onMount(()=> {
    const image = new Image();
    image.src = src;

    image.onload = () => {
      imgWidth = 400;
      imgHeight = (400 * image.height) / image.width;

      puzzlePieceWidth = imgWidth / cols;
      puzzlePieceHeight = imgHeight / rows;
    };
  })

</script>

<div class="sliding-puzzle-container">
  <!-- <img src={src} width="400" alt="Sliding Puzzle Image"> -->
  {#each rowIndices as i}
    {#each colIndices as j}
      <div 
        class="puzzle-piece" 
        style={
          ` transform: translate(${puzzlePieceWidth * j}px, ${puzzlePieceHeight * i}px);
            width: ${puzzlePieceWidth}px;
            height: ${puzzlePieceHeight}px;
          `}
      >
        {i}, {j}
      </div>
    {/each}
  {/each}
</div>

<style>
  /* img {
    width: 500px;
    height: 300px;
    background-image: url('./Assets/house.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 100px 100px; 
    background-color: red;
  } */
  .sliding-puzzle-container {
    position: relative;
  }
  .puzzle-piece {
    position: absolute;
    top: 0;
    left: 0;
    background-color: red;
  }
</style>
