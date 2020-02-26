<script>
import Doors from './components/Doors.svelte'

let sound = './lofi.mp3'
</script>

<main>
	<Doors />
	<audio src={sound} autoplay loop></audio>
</main>

<style>

:global(*) {
	box-sizing: border-box;
}

:global(html, body, main) {
	margin: 0;
	padding: 0;
}

</style>