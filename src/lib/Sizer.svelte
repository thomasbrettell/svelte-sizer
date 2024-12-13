<script module lang="ts">
	export interface Dimensions {
		width: number;
		height: number;
	}
</script>

<script lang="ts">
	import { setContext } from 'svelte';
	import { derived, writable } from 'svelte/store';

	let {
		absolute = false,
		children
	}: {
		absolute?: boolean;
		children?: any;
	} = $props();

	const ref = writable<HTMLDivElement>();

	const width = writable<number>();
	const height = writable<number>();
	const dimensions = derived([width, height], ([$width, $height]) => {
		return {
			width: $width,
			height: $height
		};
	});

	setContext('dimensions', dimensions);
	setContext('sizerRef', ref);
</script>

<div class:absolute bind:this={$ref} bind:clientWidth={$width} bind:clientHeight={$height}>
	{#if $dimensions.width && $dimensions.height && $ref}
		{@render children?.()}
	{/if}
</div>

<style>
	div {
		width: 100%;
		height: 100%;
		display: flex;
	}

	.absolute {
		position: absolute;
		top: 0;
		left: 0;
	}
</style>
