# svelte-sizer

A wrapping component which automatically passes the dimensions of its parents to its children. Ensures the dimensions are available on mount.

## Installation

This is a single file component, so just copy `src/lib/Sizer.svelte` into your project.

## Example usage

```html
<script>
	import ConsumingElement from './ConsumingElement.svelte';
	import Sizer from '$lib/Sizer.svelte';
</script>

<!-- the size of .sized-element will be available in ConsumingElement -->
<div class="sized-element">
	<Sizer>
		<ConsumingElement />
	</Sizer>
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
```

```html
<!-- ConsumingElement.svelte -->
<script lang="ts">
	import { getContext } from 'svelte';
	import type { Dimensions } from '$lib/Sizer.svelte';
	import type { Writable } from 'svelte/store';

	const dimensions = getContext<Writable<Dimensions>>('dimensions'); // access using the "dimensions" context
</script>
```

## Options

| Option     | Default | Description                            |
| ---------- | ------- | -------------------------------------- |
| `absolute` | `false` | Absolutely position the sizing element |
