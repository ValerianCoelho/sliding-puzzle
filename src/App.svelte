<script>
  import PuzzleContainer from "./Components/PuzzleContainer.svelte";

  let rows = 4;
  let cols = 4;
  let src = "https://images.unsplash.com/photo-1511884642898-4c92249e20b6?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D";
  $:width = 400; // Create a reactive statement for width

  function handleInput(source, e) {
    if (source === 'src') {
      src = e.target.value;
    } else if (source === 'rows') {
      rows = parseInt(e.target.value) || 1;
    } else if (source === 'cols') {
      cols = parseInt(e.target.value) || 1;
    }
  }


  // Update width on window resize
  window.addEventListener('resize', () => {
    width = calculateWidth(); // Call a function to calculate the new width
  });

  function calculateWidth() {
    // Add your logic to calculate the new width based on window size or any other factors
    return window.innerWidth < 500 ? window.innerWidth - 100 : 400;
  }
</script>

<main class="main">
  <PuzzleContainer
    rows={rows}
    cols={cols}
    src={src}
    width={width}
  />
  <div class="input-container">
    <input type="text" placeholder="Enter Image Link" value={src} on:input={(e) => handleInput('src', e)}>
    <input type="number" placeholder="Enter Number of Rows" value={rows} on:input={(e) => handleInput('rows', e)}>
    <input type="number" placeholder="Enter the Number of Columns" value={cols} on:input={(e) => handleInput('cols', e)}>
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
    width: calc(100% - 50px);
    padding: 20px 0;
    max-width: 450px;
  }

  input {
    outline: none;
    border: none;
    color: rgb(86, 86, 86);
    background-color: hsl(0, 0%, 88%);
    padding: 10px 5px;
    width: 100%;
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
