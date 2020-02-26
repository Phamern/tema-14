<script>
  import Clickable from './Clickable.svelte'

  let doors = [
    'door1',
    'door2',
    'door3',
  ]

</script>

<main>

  <section class="doors">
    {#each doors as door, i}
       <Clickable show='hidden' myNumber={i} />
    {/each}
  </section>

</main>


<style>
  .doors {
    display: grid;
    grid-auto-flow: column;
    place-items: center;
    height: 100vh;
    /* justify-content: center;
    align-items: end;
    padding-bottom: 10vh;
    gap: 10rem; */
  }

</style>