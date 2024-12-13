<script lang="ts">
	import { getContext } from 'svelte';
	import type { Dimensions } from '$lib/Sizer.svelte';
	import type { Writable } from 'svelte/store';

	const dimensions = getContext<Writable<Dimensions>>('dimensions');
</script>

<div>
	{$dimensions.width}, {$dimensions.height}
</div>

<style>
	div {
		background-color: red;
		border-radius: 10px;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
		color: white;
		font-weight: 900;
		font-size: 20px;
	}
</style>
