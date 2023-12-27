<script>
  import SlidingPuzzle from "./Components/SlidingPuzzle.svelte";
</script>

<main class="main">
  <SlidingPuzzle 
    gap = 1
    rows = 4
    cols = 4
    width = 600
    src = 'src/Assets/house.jpg'
  />
</main>

<style>
  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
</style>
