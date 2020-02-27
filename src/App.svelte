<script>
import Topbar from "./Topbar.svelte";
import HPmain from "./HPmain.svelte";

	window.SpeechRecognition = window.SpeechRecognition || webkitSpeechRecognition;

	const spell = new SpeechRecognition();

	spell.addEventListener('result', e => {
		const transcript = Array.from(e.results)
		.map(result => result[0])
		.map(result => result.transcript)
		.join('');

		if (transcript === "lumos") {
		document.getElementById("hp-room").src = "light-room.svg";
		}
		else if (transcript === "Knox") {
			document.getElementById("hp-room").src = "dark-room.svg";
		}

	console.log(transcript);
	});

	

	spell.addEventListener('end', spell.start);

	spell.start();
	
</script>

<main>
	<header>
		<Topbar></Topbar>
	</header>
	<div class="main">
		<HPmain></HPmain>
	</div>
</main>

<style>
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>