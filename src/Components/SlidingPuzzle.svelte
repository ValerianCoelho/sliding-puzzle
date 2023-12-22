<script>
  export let rows;
  export let cols;
  export let src;
</script>

<div>
  <img src={src} width="400" alt="Sliding Puzzle Image">
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
</style>