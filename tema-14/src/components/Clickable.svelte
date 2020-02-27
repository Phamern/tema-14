<script>

import { fade } from 'svelte/transition'
import Iris from './Iris.svelte'
import Caroline from './Caroline.svelte'
import Ena from './Ena.svelte'

export let myNumber, src

let show = false;



const hideMe = () => {
  show = !show
}

</script>

<main>
  {#if show}
     <div in:fade out:fade class="room">
      {#if myNumber === 0}
          <Caroline on:hideMe={hideMe} />
        {:else if  myNumber === 1}
          <Ena on:hideMe={hideMe} />
        {:else if  myNumber === 2}
          <Iris on:hideMe={hideMe} />
      {/if}
     </div>
  {:else}
      <div class='clickable' on:click={hideMe}>
          <img src={src} alt="doors" class='doors' />
      </div>
  {/if}
</main>

<style>

  .clickable {
    display: grid;
    place-items: center;
    gap: 1rem;
    cursor: pointer;
  }

  .doors {
    width: 15vw;
  }

</style>