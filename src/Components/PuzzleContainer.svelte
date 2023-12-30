<script>
  import SlidingPuzzle from "../Sliding Puzzle/SlidingPuzzle.svelte";
  export let rows;
  export let cols;
  export let src;
  export let width;
</script>
  
<div class="puzzle-container">
  <div class="title">D-Cipher</div>
  <div class="outer-container">
      <div class="inner-container">
        <SlidingPuzzle 
          gap = 1
          rows = {rows}
          cols = {cols}
          width = {width}
          src = {src}
        />
      </div>
  </div>
</div>

<style>
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
    @media (width < 450px) {
      padding: 20px;
    }
    
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

  