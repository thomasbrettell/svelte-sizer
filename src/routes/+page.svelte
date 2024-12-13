<script>
	import ConsumingElement from './ConsumingElement.svelte';
	import Sizer from '$lib/Sizer.svelte';
</script>

<div class="center">
	<div class="sized-element">
		<Sizer>
			<ConsumingElement />
		</Sizer>
	</div>
</div>

<style>
	.center {
		width: 100%;
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.sized-element {
		width: 90%;
		height: 90%;
		max-width: 1000px;
		max-height: 1000px;
	}
</style>
