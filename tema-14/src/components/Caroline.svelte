<script>
	import Parallax from 'parallax-js'
  import { fade } from 'svelte/transition'
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()

	let polaroid1 = ''
	let polaroid2 = ''
	let polaroid3 = ''

	let doorIcon = './images/door_icon.png';
	let backImage = './images/Caroline/caroline_background.png'

	let images = [
		'./images/Caroline/caroline_room.png',
		'./images/Caroline/caroline_drink.png',
		'./images/Caroline/caroline_food.png',
		'./images/Caroline/caroline_clothes.png',
		'./images/Caroline/caroline_character.png',
		'./images/Caroline/caroline_bed.png',
		'./images/Caroline/caroline_plant.png',
  ]
  
    let polaroid = [
      './images/Iris/iris_polaroid1.PNG',
      './images/Iris/iris_polaroid2.PNG',
      './images/Iris/iris_polaroid3.PNG',
    ]

	let parallaxInstance
	const ready = node => {
		parallaxInstance = new Parallax(node)
		parallaxInstance.scalar(20.0)
		parallaxInstance.invert(false, false)
	}

</script>

<main >
		<section>
			<img src='{backImage}' class='backImage' alt='Background' />
			<div data-pointer-events='true' use:ready>
				<div data-depth='.1'>
						<img src='{images[0]}' alt='parallax' class='room' />
				</div>
				<div data-depth='.15'>
						<img on:click={() =>  polaroid2 = !polaroid2 } src='{images[1]}' alt='parallax' class='drink'>
            {#if polaroid2}
            <section on:click={() =>  polaroid2 = !polaroid2 } in:fade out:fade class='fixed'>
              <img src='{polaroid[1]}' alt='polaroid' class='polaroid1' />
           </section>
		      {/if}
				</div>
				<div data-depth='.12'>
						<img on:click={() =>  polaroid3 = !polaroid3 } src='{images[2]}' alt='parallax' class='food'>
            {#if polaroid3}
            <section on:click={() =>  polaroid3 = !polaroid3 } in:fade out:fade class='fixed'>
              <img src='{polaroid[2]}' alt='polaroid' class='polaroid1' />
           </section>
           {/if}
				</div>
				<div data-depth='.11'>
						<img src='{images[3]}' alt='parallax' class='clothes'>
				</div>
				<div data-depth='.12'>
						<img src='{images[4]}' alt='parallax' class='character'>
				</div>
				<div data-depth='.08'>
						<img src='{images[5]}' alt='parallax' class='bed'>
				</div>
				<div data-depth='.12'>
						<img src='{images[6]}' alt='parallax' class='plant'>
				</div>
			</div>
		</section>
      <div on:click={() => dispatch('hideMe')} class='backButton'><img src='{doorIcon}' alt='doorIcon' class='door-icon'/></div>
</main>

<style>

	main {
		display: grid;
		height: 100vh;
		width: 100vw;
		place-items: center;
		overflow: hidden;
		position: fixed;
		top: 0;
		left: 0;
	}


	.backImage {
		z-index: 0;
		width: 120vw;
		position: absolute;
		top: 0vh;
	}

	.backButton {
    position: fixed;
    font-size: 2rem;
    cursor: pointer;
  }

	.door-icon {
		position: absolute;
		left: 1rem;
		top: 1rem;
		width: 35px;
	}

  .backButton {
    position: fixed;
    font-size: 2rem;
    cursor: pointer;
  }

	.room {
		width: 104vw;
		margin-left: -2vw;
		margin-top: -5vh;
		cursor: default;

	}

	.drink {
		position: absolute;
    cursor: pointer;
		width: 100px;
		top: 18vh;
    left: 8vw;
	}

	.food {
    position: absolute;
    cursor: pointer;
		width: 120px;
		top: 43.5vh;
    left: 58vw;
	}

	.clothes {
    position: absolute;
    cursor: pointer;
		width: 160px;
    top: 25vh;
		left: 28.5vw;
	}

	.character {
    position: absolute;
    cursor: pointer;
		width: 200px;
    top: 40vh;
		left: 7vw;
	}

	.bed {
    position: absolute;
    cursor: pointer;
		width: 450px;
    top: 13vh;
		left: 70vw;
	}

	.plant {
    position: absolute;
    cursor: pointer;
		width: 250px;
    top: 45vh;
		left: 35vw;
	}

	section {
		display: grid;
		place-items: center;
		font-size: 4rem;
	}

  .polaroid1 {
    width: 80vw;
    z-index: 100;
  }

</style>
