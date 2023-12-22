<script>
  export let rows = 5;
  export let cols = 5;
  export let src;

  const rowIndices = Array.from({length: 5}, (_, index) => index + 1);
  const colIndices = Array.from({length: 5}, (_, index) => index + 1);
</script>

<div class="sliding-puzzle-container">
  <!-- <img src={src} width="400" alt="Sliding Puzzle Image"> -->
  {#each rowIndices as i}
    {#each colIndices as j}
      <div 
        class="puzzle-piece" 
        style={`transform: translate(${10 * j}px, ${10 * i}px);`}
      >
        Hello</div>
    {/each}
  {/each}
</div>

<style>
  img {
    width: 500px;
    height: 300px;
    background-image: url('./Assets/house.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 100px 100px; 
    background-color: red;
  }
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
