<script>
	import Parallax from 'parallax-js'
  import { fade } from 'svelte/transition'
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()

	let polaroid1 = ''
	let polaroid2 = ''
	let polaroid3 = ''

	let doorIcon = './images/door_icon.png';
	let backImage = './images/Ena/ena_background.png'

	let images = [
		'./images/Ena/ena_room.gif',
		'./images/Ena/ena_books_plushie.png',
		'./images/Ena/ena_carpet.png',
		'./images/Ena/ena_sacco.png',
		'./images/Ena/ena_bottle.png',
		'./images/Ena/ena_shiba_plant.png',
		'./images/Ena/ena_table_pillow.png',
		'./images/Ena/ena_tall_plant.png',
		'./images/Ena/ena_character.gif',
		'./images/Ena/ena_cat.gif',
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
						<img on:click={() =>  polaroid2 = !polaroid2 } src='{images[2]}' alt='parallax' class='carpet'>
            {#if polaroid2}
            <section style='z-index: 100;' on:click={() =>  polaroid2 = !polaroid2 } in:fade out:fade class='fixed'>
              <img style='z-index: 100;' src='{polaroid[1]}' alt='polaroid' class='polaroid1' />
           </section>
		      {/if}
				</div>
				<div data-depth='.22'>
						<img on:click={() =>  polaroid3 = !polaroid3 } src='{images[3]}' alt='parallax' class='sacco'>
            {#if polaroid3}
            <section on:click={() =>  polaroid3 = !polaroid3 } in:fade out:fade class='fixed'>
              <img src='{polaroid[2]}' alt='polaroid' class='polaroid1' />
           </section>
           {/if}
				</div>
				<div data-depth='.24'>
						<img src='{images[9]}' alt='parallax' class='cat'>
				</div>
				<div data-depth='.12'>
						<img src='{images[6]}' alt='parallax' class='pillow'>
				</div>
				<div data-depth='.08'>
						<img src='{images[4]}' alt='parallax' class='bottle'>
				</div>
				<div data-depth='.12'>
						<img src='{images[5]}' alt='parallax' class='plant'>
				</div>
				<div data-depth='.12'>
						<img src='{images[7]}' alt='parallax' class='tall-plant'>
				</div>
				<div data-depth='.12'>
						<img src='{images[8]}' alt='parallax' class='character'>
				</div>
				<div data-depth='.28'>
					<img on:click={() =>  polaroid1 = !polaroid1 } src='{images[1]}' alt='parallax' class='books' />
          {#if polaroid1}
            <section on:click={() =>  polaroid1 = !polaroid1 } in:fade out:fade class='fixed'>
              <img src='{polaroid[2]}' alt='polaroid' class='polaroid1' />
           </section>
		      {/if}
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

	.books {
		position: absolute;
    cursor: pointer;
		width: 450px;
		top: 65vh;
    left: 40vw;
	}

	.carpet {
    position: absolute;
    cursor: pointer;
		width: 480px;
		top: 77vh;
    left: 25vw;
	}

	.sacco{
    position: absolute;
    cursor: pointer;
		width: 240px;
    top: 63vh;
		left: 17vw;
	}

	.bottle {
    position: absolute;
    cursor: pointer;
		width: 60px;
    top: 68vh;
		left: 75vw;
	}

	.plant {
    position: absolute;
    cursor: pointer;
		width: 300px;
    top: 55vh;
		left: 85vw;
	}

	.pillow {
    position: absolute;
    cursor: pointer;
		width: 350px;
    top: 73vh;
		left: 65vw;
	}

	.tall-plant {
    position: absolute;
    cursor: pointer;
		width: 550px;
    top: 45vh;
		left: -10vw;
	}

	.character {
    position: absolute;
    cursor: pointer;
		width: 230px;
    top: 56vh;
		left: 38vw;
	}

	.cat {
    position: absolute;
    cursor: pointer;
		width: 90px;
    top: 66vh;
		left: 22vw;
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
