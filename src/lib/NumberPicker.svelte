<script>
	import { onMount } from 'svelte';

	export let numbers;
	export let current;

	const delay = 200;
	let timeout = null;
	let box;

	const onScroll = function() {
		clearTimeout(timeout);
		timeout = setTimeout(() => {
			const scrollTop = box.scrollTop;
			const digitElementHeight = box.firstChild.clientHeight;
			const halfWayElemPos = digitElementHeight + scrollTop;
      const closestElemIndex = Math.round(halfWayElemPos / digitElementHeight) -1;
      scrollToIndex(closestElemIndex);
		}, delay);
	};
	const scrollToIndex = (index) => {
		const digitHeight = box.firstChild.clientHeight;

		//box.scroll(0, parseInt(index * digitHeight));
		box.scroll({
			left: 0,
			top: index * digitHeight,
			behavior: 'smooth'
		});
		current = index;
	};

	function scroll() {
		scrollToIndex(4);
	}

	onMount(() => scrollToIndex(current));
</script>

<div class="number-picker">
	<button on:click={() => scrollToIndex(current - 1)} disabled={current < 1} class="selector">&minus;</button>

	<div class="digit-wrapper">
		<ul bind:this={box} class="digits" on:scroll={onScroll}>
			{#each numbers as number, index}
			<li class="digit" class:active={index === current}>{number}</li>
			{/each}
		</ul>
		<span class="half half-left"></span>
		<span class="half half-right"></span>
	</div>

	<button on:click={() => scrollToIndex(current + 1)} disabled={current === numbers.length - 1} class="selector">&plus;</button>
</div>

<style>
	* {
		-webkit-box-sizing: border-box;
  	box-sizing: border-box;
  	margin: 0;
	  padding: 0;
	}

	.digit-wrapper {
		position: relative;
		text-align: center;
		border: 1px solid black;
		font-size: 1.5rem;
		min-width: 5rem;
		height: 4.5rem;
	}

	.selector {
		min-width: 5rem;
		padding: 1rem;
		width: 100%;
	}

	.digits {
		list-style: none;
		display: block;
		line-height: 2.25rem;
		height: 100%;
		overflow-y: scroll;
		-webkit-overflow-scrolling: touch;
		padding-top: 1.1rem;
		padding-bottom: 1.1rem;
	}

	.digit {
		height: 2.2rem;
		color: #dcdcdc;
	}

	.digit.active {
		color: black;
	}

	.half {
		position: absolute;
		display: block;
		width: 10px;
		height: 1px;
		background-color: black;
		top: 50%;
	}

	.half-left {
		left: 0;
	}

	.half-right {
		right: 0;
	}
</style>