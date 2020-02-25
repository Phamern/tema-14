<script>
import Iris from './Iris.svelte'
import Caroline from './Caroline.svelte'
import Ena from './Ena.svelte'

export let myNumber;

let show = false;

const hideMe = () => {
  show = !show
}

</script>

<main>
  {#if show}
     <div class="firstRoom">
      {#if myNumber === 0}
          <Iris on:hideMe={hideMe} />
        {:else if  myNumber === 1}
          <Caroline on:hideMe={hideMe} />
        {:else if  myNumber === 2}
          <Ena on:hideMe={hideMe} />
      {/if}
     </div>
  {:else}
    <div class='clickable' on:click={hideMe}></div>
  {/if}
</main>

<style>
  .clickable {
    height: 100px;
    width: 100px;
    background-color: blue;
  }
</style>