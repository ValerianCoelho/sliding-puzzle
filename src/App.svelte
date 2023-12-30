<script>
  import PuzzleContainer from "./Components/PuzzleContainer.svelte";

  $:rows = 4;
  $:cols = 4;
  $:src = "src/Assets/house.jpg"

  function handleInput(source, e) {
    if(source === 'src') {
      src = e.target.value
    }
    else if(source === 'rows') {
      rows = parseInt(e.target.value) || 1;
    }
    else if(source === 'cols') {
      cols = parseInt(e.target.value) || 1;
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
    <input type="text" placeholder="Enter Image Link" value={src} on:input={(e)=>handleInput('src', e)}>
    <input type="number" placeholder="Enter Number of Rows" value={rows} on:input={(e)=>handleInput('rows', e)}>
    <input type="number" placeholder="Enter the Number of Columns" value={cols} on:input={(e)=>handleInput('cols', e)}>
  </div>
</main>

<style>
  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    user-select: none;
  }
  :global(body) {
    background-color: #E0E0E0;
  }

  .main {
    margin-top: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .input-container {
    display: flex;
    flex-direction: column;
    gap: 4px;
    padding: 16px;
  }

  input {
    outline: none;
    border: none;
    color: rgb(86, 86, 86);
    background-color: hsl(0, 0%, 88%);
    padding: 10px 5px;
    width: 450px;
    border-radius: 10px;
    box-shadow: 2px 2px 7px 0px rgba(0, 0, 0, 0.25), 
                1px 1px 2px 0px rgba(0, 0, 0, 0.25), 
                -1px -1px 2.1px 0px #FFF, 
                -2px -2px 0.8px 0px #FFF;
    transition: box-shadow 0.3s ease-in-out;
  }

  input:focus {
    box-shadow: 1.5px 1.5px 7px 0px rgba(0, 0, 0, 0.25), 
                1px 1px 1.5px 0px rgba(0, 0, 0, 0.25), 
                -1px -1px 2.1px 0px #FFF, 
              -1.5px -1.5px 0.8px 0px #FFF;
  }
</style>
