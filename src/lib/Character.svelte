<script>
	import NumberPicker from '$lib/NumberPicker.svelte';

	export let name;
	export let traits;

	const speed = traits.speed.values;
	const speedIndex = traits.speed.startingIndex;
	const might = traits.might.values;
	const mightIndex = traits.might.startingIndex;
	const sanity = traits.sanity.values;
	const sanityIndex = traits.sanity.startingIndex;
	const knowledge = traits.knowledge.values;
	const knowledgeIndex = traits.knowledge.startingIndex;
</script>

<div class="descriptors">
	<h1 class="name">{name}</h1>
</div>


<div class="wrapper">
	<div>
		<span>Might</span>
		<NumberPicker numbers={might} current={mightIndex}></NumberPicker>
	</div>
	<div>
		<span>Sanity</span>
		<NumberPicker numbers={sanity} current={sanityIndex}></NumberPicker>
	</div>
	<div>
		<span>Speed</span>
		<NumberPicker numbers={speed} current={speedIndex}></NumberPicker>
	</div>
	<div>
		<span>Knowledge</span>
		<NumberPicker numbers={knowledge} current={knowledgeIndex}></NumberPicker>	</div>
</div>


<style>
	.descriptors {
		margin: auto;
		max-width: 720px;
	}

	.wrapper {
		margin: auto;
		max-width: 720px;
		display: grid;
		gap: 1rem;
		grid-template: 1fr 1fr / 1fr 1fr;
	}
</style>
