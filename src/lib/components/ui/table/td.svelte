<script lang="ts">
	import type { HTMLTdAttributes } from 'svelte/elements'
	interface Props extends HTMLTdAttributes {
		noPadding?: boolean
	}
	let { noPadding = false, children, ...restProps }: Props = $props()
</script>

<td class:noPadding {...restProps}>
	{#if children}
		{@render children()}
	{/if}
</td>

<style lang="postcss">
	td {
		appearance: none;
		padding: var(--three-quarters-padding);
		color: var(--colors-ultra-high);
		font-size: var(--font-size);
		line-height: var(--line-height);
		font-family: var(--font-family-sans-serif);
		letter-spacing: var(--letter-spacing);
		text-align: left;
		&.noPadding {
			padding: 0;
		}
	}
</style>
