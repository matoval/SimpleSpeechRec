<script>
import Topbar from "./Topbar.svelte";
import Bottombar from "./Bottombar.svelte";
	
</script>

<main>
	<header>
		<Topbar></Topbar>
	</header>
	<div class="main">
	</div>
	<footer>
		<Bottombar></Bottombar>
	</footer>
</main>

<style>
	.main {
		min-height: 95vh;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>