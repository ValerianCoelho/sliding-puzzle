<script>
  import PuzzleContainer from "./Components/PuzzleContainer.svelte";

  $:rows = 3;
  $:cols = 4;
  $:src = "src/Assets/house.jpg"

  function handleInput(source, e) {
    if(source === 'src') {
      src = e.target.value
    }
    else if(source === 'rows') {
      rows = parseInt(e.target.value);
    }
    else if(source === 'cols') {
      cols = parseInt(e.target.value);
    }
  }
</script>

<main class="main">
  <PuzzleContainer
    rows={rows}
    cols={cols}
    src={src}
  />
  <div class="input-container">
    <input type="text" placeholder="Enter Image Link" on:input={(e)=>handleInput('src', e)}>
    <input type="number" placeholder="Enter Number of Rows" on:input={(e)=>handleInput('rows', e)}>
    <input type="number" placeholder="Enter the Number of Columns" on:input={(e)=>handleInput('cols', e)}>
  </div>
</main>

<style>
  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    user-select: none;
  }
  .main {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100vh;
    background-color: #E0E0E0;
  }
  .input-container {
    display: flex;
    flex-direction: column;
    gap: 4px;
    padding: 16px;
  }
  input {
    outline: none;
    border: 1px solid rgba(0, 0, 0, 0.5);
    background-color: #E0E0E0;
    padding: 10px 5px;
    width: 450px;
    border-radius: 5px;
  }
</style>
