<script>
	import characters from '$lib/characters';
</script>

<div class="content">
	<h1>Characters</h1>
	<ul>
		{#each characters as character, index (character.name)}
			<li>
				<a href="/c/{index}">{character.name}</a>
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
