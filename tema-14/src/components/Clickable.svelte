<script>

import { fade } from 'svelte/transition'
import Iris from './Iris.svelte'
import Caroline from './Caroline.svelte'
import Ena from './Ena.svelte'

export let myNumber;

let show = false;

let doors = [
  './images/Iris/iris_door.PNG',
  // './images/Iris/iris_computer.PNG',
  // './images/Iris/iris_mirror.PNG',
]

const hideMe = () => {
  show = !show
}

</script>

<main>
  {#if show}
     <div in:fade out:fade class="room">
      {#if myNumber === 0}
          <Iris on:hideMe={hideMe} />
        {:else if  myNumber === 1}
          <Caroline on:hideMe={hideMe} />
        {:else if  myNumber === 2}
          <Ena on:hideMe={hideMe} />
      {/if}
     </div>
  {:else}
    {#each doors as door, i}
      <div class='clickable' on:click={hideMe}>
          <img src={doors[i]} alt="doors" class='doors' />
      </div>
    {/each}
  {/if}
</main>

<style>

  .clickable {
    display: grid;
    place-items: center;
    gap: 1rem;
  }

  .doors {
    width: 15vw;
  }

</style>