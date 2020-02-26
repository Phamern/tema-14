<script>
	import Parallax from 'parallax-js'
  import { fade } from 'svelte/transition'
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()

	let polaroid1 = ''
	let polaroid2 = ''
	let polaroid3 = ''

	let backImage = './images/Iris/iris_background.png'

  
	let images = [
		'./images/Iris/iris_room.PNG',
		'./images/Iris/iris_mirror.PNG', 
		'./images/Iris/iris_character.PNG', 
		'./images/Iris/iris_computer.PNG', 
		'./images/Iris/iris_forground1.PNG', 
		'./images/Iris/iris_forground2.PNG', 
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
						<img src='{images[0]}' alt='parallax' class='image0' />
				</div>
				<div data-depth='.28'>
					<img on:click={() =>  polaroid1 = !polaroid1 } src='{images[1]}' alt='parallax' class='image1' />
          {#if polaroid1}
            <section style='z-index: 100;' on:click={() =>  polaroid1 = !polaroid1 } in:fade out:fade class='fixed'>
              <img style='z-index: 100;' src='{polaroid[0]}' alt='polaroid' class='polaroid1' />
           </section>
		      {/if}
				</div>
				<div data-depth='.2'>
						<img on:click={() =>  polaroid2 = !polaroid2 } src='{images[2]}' alt='parallax' class='image2'>
            {#if polaroid2}
            <section style='z-index: 100;' on:click={() =>  polaroid2 = !polaroid2 } in:fade out:fade class='fixed'>
              <img style='z-index: 100;' src='{polaroid[1]}' alt='polaroid' class='polaroid1' />
           </section>
		      {/if}
				</div>
				<div data-depth='.3'>
						<img on:click={() =>  polaroid3 = !polaroid3 } src='{images[3]}' alt='parallax' class='image3'>
            {#if polaroid3}
            <section style='z-index: 100;' on:click={() =>  polaroid3 = !polaroid3 } in:fade out:fade class='fixed'>
              <img style='z-index: 100;' src='{polaroid[2]}' alt='polaroid' class='polaroid1' />
           </section>
           {/if}
				</div>
				<div data-depth='.08'>
						<img src='{images[4]}' alt='parallax' class='image4'>
				</div>
				<div data-depth='.12'>
						<img src='{images[5]}' alt='parallax' class='image5'>
				</div>
			</div>
		</section>
			<!-- <h1 on:click={() =>  info = !info } class='clickinfo'>Info</h1> -->
      <div on:click={() => dispatch('hideMe')} class='backButton'>Back</div>
		<!-- <section>
			{#if info}
        <section on:click={() =>  info = !info } in:fade out:fade class='fixed'>
          <img src='{polaroid[0]}' alt='polaroid' class='polaroid' />
        </section>
			{/if}
		</section> -->
</main>

<style>

	main {
		display: grid;
		height: 100vh;
		width: 100vw;
		place-items: center;
		overflow: hidden;
		position: relative;
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
		width: 110vw;
		margin-left: -5vw;
		margin-top: -2vh;

	}

	.image1 {
		position: absolute;
    cursor: pointer;
		width: 80px;
		/* z-index: 4; */
		top: 40vh;
    left: 6vw;
	}

	.image2 {
    position: absolute;
    cursor: pointer;
		/* z-index: 4; */
		width: 580px;
		top: 70vh;
    left: 25vw;
	}

	.image3 {
    position: absolute;
    cursor: pointer;
		/* z-index: 4; */
		width: 600px;
    top: 30vh;
		left: 57vw;
	}

	.image4 {
    position: absolute;
    cursor: pointer;
		/* z-index: 4; */
		width: 400px;
    top: 67vh;
		left: -2vw;
	}

	.image5 {
    position: absolute;
    cursor: pointer;
		/* z-index: 4; */
		width: 450px;
    top: 70vh;
		left: 78vw;
	}

	/* .clickinfo {
		cursor: pointer;
		z-index: 5;
		font-size: 4rem;
		position: fixed;
    top: 20vh;
	} */

	section {
		display: grid;
		place-items: center;
		font-size: 4rem;
	}

  .polaroid1 {
    width: 80vw;
    z-index: 100;
  }

	/* .fixed {
		position: fixed;
		top: 0;
		left: -2rem;
		color: white;
	} */

</style>
