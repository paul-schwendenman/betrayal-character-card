<script>
	import characters from '$lib/characters';
</script>

<svelte:head>
	<title>Betrayal at the House on the Hill: Characters</title>
</svelte:head>

<div class="content">
	<h1>Characters</h1>
	<ul>
		{#each characters as character, index (character.name)}
			<li>
				<a href="/c/{index}">{character.name} </a>
				<!-- speed: {character.traits.speed.values[character.traits.speed.startingIndex]} -->
				<!-- might: {character.traits.might.values[character.traits.might.startingIndex]} -->
				<!-- sanity: {character.traits.sanity.values[character.traits.sanity.startingIndex]} -->
				<!-- knowledge: {character.traits.knowledge.values[character.traits.knowledge.startingIndex]} -->
			</li>
		{/each}
	</ul>
</div>

<style>
	.content {
		margin: auto;
		max-width: 720px;
	}

	ul {
		list-style: none;
	}
</style>
