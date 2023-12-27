<script>
  import SlidingPuzzle from "./Components/SlidingPuzzle.svelte";
</script>

<main class="main">
  <div class="puzzle-container">
    <div class="title">D-Cipher</div>
    <div class="outer-container">
      <div class="inner-container">
        <SlidingPuzzle 
          gap = 1
          rows = 4
          cols = 4
          width = 400
          src = 'src/Assets/house.jpg'
        />
      </div>
    </div>
  </div>
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
    flex-direction: column;
    height: 100vh;
    background-color: #E0E0E0;
  }
  .title {
    font-family: 'Inria Serif';
    margin-right: auto;
    display: inline-block;
    padding: 10px;
    color: rgba(0, 0, 0, 0.5);
    margin-bottom: 5px;
    border-radius: 4px;
    box-shadow: 2px 2px 7px 0px rgba(0, 0, 0, 0.25), 
                1px 1px 2px 0px rgba(0, 0, 0, 0.25), 
                -1px -1px 2.1px 0px #FFF, 
                -2px -2px 0.8px 0px #FFF;
  }
  .outer-container {
    padding: 24px;
    border-radius: 6px;
    background: #E0E0E0;
    box-shadow: 2px 2px 7px 0px rgba(0, 0, 0, 0.25), 
                1px 1px 2px 0px rgba(0, 0, 0, 0.25), 
                -1px -1px 2.1px 0px #FFF, 
                -2px -2px 0.8px 0px #FFF;
  }
  .inner-container {
    background-color: blue;
    padding: 1px;
    border-radius: 2px;
    background: #E0E0E0;
    box-shadow: 2px 2px 4.2px 0px #FFF, 
                1px 1px 1.6px 0px #FFF, 
                -1px -1px 1.3px 0px rgba(0, 0, 0, 0.25), 
                -0.5px -0.5px 0.8px 0px rgba(0, 0, 0, 0.25);
  }
</style>
