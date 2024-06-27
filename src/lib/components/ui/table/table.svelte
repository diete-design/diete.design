<script lang="ts">
	import type { HTMLAttributes } from 'svelte/elements'
	let { children, ...restProps }: HTMLAttributes<HTMLElement> = $props()
</script>

<table {...restProps}>
	{#if children}
		{@render children()}
	{/if}
</table>

<style lang="postcss">
	table {
		border-collapse: collapse;
		border-spacing: 0;
		width: 100%;
		table-layout: fixed;
	}
</style>
