<script lang="ts">
	import type { HTMLThAttributes } from 'svelte/elements'
	interface Props extends HTMLThAttributes {
		noPadding?: boolean
	}
	let { noPadding = false, children, ...restProps }: Props = $props()
</script>

<th class:noPadding {...restProps}>
	{#if children}
		{@render children()}
	{/if}
</th>

<style lang="postcss">
	th {
		appearance: none;
		padding: var(--three-quarters-padding);
		color: var(--colors-ultra-high);
		font-weight: var(--font-weight-h5);
		font-size: var(--font-size-h5);
		line-height: var(--line-height-h5);
		font-family: var(--font-family-sans-serif);
		letter-spacing: var(--letter-spacing-h5);
		text-align: left;
		&.noPadding {
			padding: 0;
		}
	}
</style>
