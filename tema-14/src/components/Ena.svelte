<script>
	import Parallax from 'parallax-js'
  import { fade } from 'svelte/transition'
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()

	let info = ''

	let backImage = './images/Layer_4.png'
  let polaroid = './images/Polaroid1.png'
  
	let images = [
		'./images/Ena/ena_background.png',
		'./images/Midground.png', 
		'./images/Character.png', 
	]

	let parallaxInstance
	const ready = node => {
		parallaxInstance = new Parallax(node)
		parallaxInstance.scalar(20.0)
		parallaxInstance.invert(false, false)
	}

</script>

<main>
		<section>
			<img src='{backImage}' class='backImage' alt='Background' />
			<div data-pointer-events='true' use:ready>
				<div data-depth='.1'>
						<img src='{images[0]}' alt='parallax' class='image0' />
				</div>
				<div data-depth='.28'>
						<img src='{images[1]}' alt='parallax' class='image1' />
				</div>
				<div data-depth='.2'>
						<img src='{images[2]}' alt='parallax' class='image2'>
				</div>
			</div>
		</section>
			<h1 on:click={() =>  info = !info } class='clickinfo'>Info</h1>
      <div on:click={() => dispatch('hideMe')} class='backButton'>Back</div>
		<section>
			{#if info}
        <section in:fade out:fade class='fixed'>
          <img src='{polaroid}' alt='polaroid' />
        </section>
			{/if}
		</section>
</main>

<style>

	main {
		display: grid;
		height: 100vh;
		width: 100vw;
		/* place-items: center; */
		overflow: hidden;
		position: absolute;
    top: 0;
    left: 0;
	}

	.backImage {
		z-index: 0;
		width: 100vw;
		position: absolute;
		top: 0vh;
	}

  .backButton {
    position: fixed;
    font-size: 2rem;
    cursor: pointer;
  }

	.image0 {
		width: 130vw;
		margin-left: -15vw;
		margin-top: -2vh;

	}
	.image1 {
		/* width: 40vw; */
		margin-top: 20vh;
		width: 100vw;
		z-index: 4;
		margin: 6vh 0 0 -2vw;
	}
	.image2 {
		z-index: 4;
		width: 100vw;
		margin-top: 17vh;
	}
	/* .image3 {
		z-index: 4;
		width: 110vw;
		margin-left: 65vw;
	} */

	.clickinfo {
		cursor: pointer;
		z-index: 5;
		font-size: 4rem;
		position: fixed;
	}
	.clickinfo {
		cursor: pointer;
		z-index: 5;
		font-size: 4rem;
		position: fixed;
    top: 20vh;
	}

	section {
		display: grid;
		place-items: center;
		font-size: 4rem;
	}

	.fixed {
		/* width: 30rem;
		height: 40rem;
		background-color: lightblue; */
		position: fixed;
		top: 0;
		left: -2rem;
		color: white;
	}

</style>
