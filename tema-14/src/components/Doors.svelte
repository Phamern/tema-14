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
</style>