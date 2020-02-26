<script>
  import Clickable from './Clickable.svelte'

  let doors = [
    'door1',
    'door2',
    'door3',
  ]

</script>

<main>
<h1>overtenking</h1>
  <section class="doors">
    {#each doors as door, i}
       <Clickable show='hidden' myNumber={i} />
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
    margin:0;
    padding: 0;
  }
  .doors {
    display: grid;
    grid-auto-flow: column;
    place-items: center;
    height: 100vh;
    cursor: pointer;
    /* justify-content: center;
    align-items: end;
    padding-bottom: 10vh;
    gap: 10rem; */
  }

</style>