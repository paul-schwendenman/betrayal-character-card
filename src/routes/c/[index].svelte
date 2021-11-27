<script context="module">
import characters from "$lib/characters";


	export async function load({ page }) {
		const { index } = page.params;

		const character = characters[index];

		return {
			props: { character }
		};
	}
</script>

<script>
	import Character from "$lib/Character.svelte";

	export let character;
</script>

<svelte:head>
	<title>Betrayal at the House on the Hill: {character.name}</title>
</svelte:head>

<Character {...character}></Character>
