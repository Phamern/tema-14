<script>
  import Clickable from './Clickable.svelte'

  let doors = [
  './images/Caroline/caroline_door.png',
  './images/Ena/ena_door.png',
  './images/Iris/iris_door.PNG',
]

</script>

<main>
  <h1>Overtenking</h1>
  <section class="doors">
    {#each doors as door, i}
       <Clickable  src='{doors[i]}' show='hidden' myNumber={i}/>
    {/each}
  </section>

</main>


<style>
  main {
    background-color: hotpink;
    overflow: hidden;
    display: grid;
  }

  h1 {
    margin: 0;
    padding: 0;
    justify-self: center;
    
  }

  .doors {
    display: grid;
    grid-auto-flow: column;
    place-items: center;
    height: 100vh;
    /* cursor: pointer; */
  }

</style>